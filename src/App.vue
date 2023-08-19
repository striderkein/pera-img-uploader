<script setup>
import ImageUploader from '@/components/organisms/ImageUploader.vue'
</script>

<template>
  <header>
    <div class="logo-container">
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="250" height="250" />
    </div>
  </header>

  <main>
    <image-uploader />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo {
  display: block;
  /* width: 100%; */
  margin: 0 auto 2rem;
}

@media (min-width: 768px) {
  header {
    display: flex;
    /* place-items: center; */
    /* padding-right: calc(var(--section-gap) / 2); */
    justify-content: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
