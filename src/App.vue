<script setup>
import ImageUploader from '@/components/organisms/ImageUploader.vue'
</script>

<template>
  <header>
    <div class="logo-container">
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="250" height="250" />
    </div>
  </header>

  <main class="body-main">
    <image-uploader />
  </main>
</template>

<style lang="scss" scoped>
@import './assets/_variables';
@import './assets/_breakpoints';

header {
  line-height: 1.5;

  @media (min-width: #{ $breakpoint-ipad }) {
    display: flex;
    /* place-items: center; */
    /* padding-right: calc(var(--section-gap) / 2); */
    justify-content: center;

    .wrapper {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  }
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

.body-main {
  max-width: $max-width-app;
  display: flex;
  justify-content: center;
  margin: 0 auto;
}

@media (min-width: $breakpoint-ipad) {
  header {
    display: flex;
    /* place-items: center; */
    /* padding-right: calc(var(--section-gap) / 2); */
    justify-content: center;
  }

  .logo {
    margin: 0 2rem 0 0;
  }
}
</style>
