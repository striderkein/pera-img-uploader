<script setup>
import PeraImage from '@/components/molecules/PeraImage.vue'

defineProps({
  images: {
    type: [Object],
    required: true
  }
})
</script>

<template>
  <span>
    <ul v-if="images.length" class="fuga">
      <li v-for="(image, index) in images" :key="image.id">
        <pera-image
          :image="image"
          :index="index"
          @left="$emit('left', index)"
          @right="$emit('right', index)"
          @delete="$emit('delete', index)"
        />
      </li>
    </ul>
    <div v-else class="no-image">
      <span class="text">画像を選択（またはドラッグアンドドロップ）してください</span>
    </div>
  </span>
</template>

<style lang="scss" scoped>
@import '../../assets/_variables.scss';

.fuga {
  width: 100%;
  list-style: none;
  display: flex;
  justify-content: flex-start;
  padding: 0;

  li:not(:last-child) {
    margin-right: $margin-each-images;
  }
}
</style>
