<script setup>
import PeraImageList from '@/components/organisms/PeraImageList.vue'
import UploadButton from '@/components/atoms/UploadButton.vue'

// TODO: implement
const images = [
  {
    id: 1,
    thumbnail: 'https://placehold.jp/320x320.png',
  },
  {
    id: 2,
    thumbnail: 'https://placehold.jp/320x320.png',
  },
  {
    id: 3,
    thumbnail: 'https://placehold.jp/320x320.png',
  },
  {
    id: 4,
    thumbnail: 'https://placehold.jp/320x320.png',
  }
]
</script>

<template>
  <div class="uploader">
    <span class="leading-text">商品写真</span>
    <span class="foo">
      <pera-image-list class="thumbnails" :images="images" />
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
  background-color: #FAFAFB; /* spoited */
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

@media (min-width: 1024px) {
  .uploader h1,
  .uploader h3 {
    text-align: left;
  }
}
</style>
