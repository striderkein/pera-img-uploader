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
  <span class="hoge">
    <ul class="fuga">
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
  </span>
</template>

<style lang="scss" scoped>
.fuga {
  list-style: none;
  display: flex;
  justify-content: center;

  li:not(:last-child) {
    margin-right: 20px;
  }
}
</style>
