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
          @delete="$emit('delete', index)"
        />
      </li>
    </ul>
  </span>
</template>

<style scoped>
.fuga {
  list-style: none;
  display: flex;
  justify-content: center;
}

.fuga li:not(:last-child) {
  margin-right: 20px;
}
</style>
