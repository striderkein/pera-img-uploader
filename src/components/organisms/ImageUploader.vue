<script setup>
import { ref } from 'vue'
import axios from 'axios'

import PeraImageList from '@/components/organisms/PeraImageList.vue'
import UploadButton from '@/components/atoms/UploadButton.vue'
import IconFolderOpen from '@/components/icons/IconFolderOpen.vue'

const images = ref([]);
const isEnter = ref(false);

const readFile = (file) => {
  return new Promise((resolve, reject) => {
    const reader = new FileReader()
    reader.onload = (e) => {
      const image = e.target.result
      resolve(image)
    }
    reader.readAsDataURL(file)
  })
}

const onFileSelect = (e) => {
  isEnter.value = false;
  const files = e.target.files || e.dataTransfer.files
  if (e.target instanceof HTMLInputElement) {
    console.log(`e.target is not HTMLInputElement`)
    return
  }

  for (const file of files) {
    readFile(file).then((image) => {
      images.value.push({
        id: images.value.length + 1,
        thumbnail: image
      })
    })
  }
}

const upload = () => {
  let params = new URLSearchParams();
  params.append('images', images.value);
  axios.post('https://httpbin.org/post', params).then(() => {
    console.log('post通信に成功しました');
  });
};

const dragEnter = () => {
  console.log(`dragEnter`)
  isEnter.value = true;
}

const dragLeave = () => {
  console.log(`dragLeave`)
  isEnter.value = false;
}

const deleteFile = (index) => {
  images.value.splice(index, 1)
}

const moveToLeft = (passedIndex) => {
  images.value.splice(passedIndex - 1, 0, images.value.splice(passedIndex, 1)[0]);
}

const moveToRight = (passedIndex) => {
  images.value.splice(passedIndex + 1, 0, images.value.splice(passedIndex, 1)[0]);
}
</script>
<template>
  <div class="uploader">
    <span class="leading-text">商品写真</span>
    <span class="foo">
      <div
        class="drop-area"
        @dragenter="dragEnter"
        @dragleave="dragLeave"
        @dragover.prevent
        @drop.prevent="onFileSelect"
        :class="{enter: isEnter}"
      >
        <span v-if="!images.length">画像を選択（またはドラッグアンドドロップ）してください</span>
        <pera-image-list
          v-else
          :images="images"
          @left="moveToLeft"
          @right="moveToRight"
          @delete="deleteFile"
        />
      </div>
      <div class="file-upload-area">
        <label for="file-upload" class="label-upload">
          <span class="icon"><icon-folder-open /></span>ファイルを選択する
          <input type="file" accept="image/*" id="file-upload" @change="onFileSelect" ref="file">
        </label>
      </div>
      <div class="button-area">
        <upload-button
          class="upload-button"
          text="保存"
          :isDisable="!images.length"
          @click="upload"
        />
      </div>
    </span>
  </div>
</template>

<style lang="scss" scoped>
@import '../../assets/_variables.scss';

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.uploader {
  width: 100%;
  height: 600px;
  display: flex;
  justify-content: center;
  flex-direction: row;
}

.uploader h1,
.uploader h3 {
  text-align: center;
}

.leading-text {
  width: $percentage-of-leading-text;
  padding: 20px;
  background-color: #fafafb; /* spoited */
  color: #333;
  font-weight: bold;
}

.foo {
  width: $percentage-of-image-area;
  padding: 30px 0;
}

.drop-area {
  $padding-vertical: 10px;

  box-sizing: border-box;
  width: 100%;
  height: calc(#{$side-length-of-image} + #{$padding-vertical} * 2);
  display: flex;
  flex-direction: row;
  overflow: scroll hidden;
  margin-left: 20px;
  padding: $padding-vertical 20px;
  background-color: #eee;
  border: 2px solid #ccc;
}

.enter {
  border: 10px dotted powderblue;
}

.button-area {
  padding: 20px 10vw;
}

.file-upload-area {
  display: flex;
  justify-content: start;
  flex-direction: row;
  padding: 20px;
}

.icon {
  width: 20px;
  height: 20px;
  margin-right: 10px;
}

.label-upload {
  display: flex;
  align-items: center;
  border: 2px solid #aaa;
  border-radius: 3px;
  padding: 3px;
  background-color: #ececed; /* spoited */
}

.label-upload > input {
  display: none;
}

@media (min-width: 1024px) {
  .uploader h1,
  .uploader h3 {
    text-align: left;
  }
}
</style>
