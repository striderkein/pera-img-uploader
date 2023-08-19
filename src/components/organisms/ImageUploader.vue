<script setup>
import { ref } from 'vue'
import PeraImageList from '@/components/organisms/PeraImageList.vue'
import UploadButton from '@/components/atoms/UploadButton.vue'
import IconFolderOpen from '@/components/icons/IconFolderOpen.vue'

const images = ref([]);

const onFileSelect = (e) => {
  const files = e.target.files
  if (e.target instanceof HTMLInputElement) {
    if (files.length > 0) {
      const file = files[0]
      const reader = new FileReader()
      reader.onload = (e) => {
        const image = e.target.result
        images.value.push({
          id: images.value.length + 1,
          thumbnail: image
        })
      }
      reader.readAsDataURL(file)
    }
  } else {
    console.log(`e.target is not HTMLInputElement`)
  }
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
      <pera-image-list
        class="thumbnails"
        :images="images"
        @left="moveToLeft"
        @right="moveToRight"
        @delete="deleteFile"
      />
      <div class="file-upload-area">
        <label for="file-upload" class="label-upload">
          <span class="icon"><icon-folder-open /></span>ファイルを選択する
          <input type="file" accept="image/*" id="file-upload" @change="onFileSelect" ref="file">
        </label>
      </div>
      <div class="button-area">
        <upload-button class="upload-button" text="保存" />
      </div>
    </span>
  </div>
</template>

<style scoped>
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
  width: 20vw;
  padding: 20px;
  background-color: #fafafb; /* spoited */
  color: #333;
  font-weight: bold;
}

.foo {
  padding: 30px 0;
}

.thumbnails {
  width: 80vw;
  display: flex;
  justify-content: center;
  flex-direction: row;
}

.button-area {
  padding: 20px 400px;
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
