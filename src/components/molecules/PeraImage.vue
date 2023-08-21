<script setup>
import SquareImage from '@/components/atoms/SquareImage.vue'
import EditButton from '@/components/atoms/EditButton.vue'

defineProps({
  image: {
    type: Object,
    required: true
  },
  index: {
    type: Number,
    required: true
  },
})
</script>

<template>
  <span class="pera-image">
    <square-image
      class="thumbnail"
      :image="image"
    />
    <edit-button
      class="edit-button"
      :index="index"
      @left="$emit('left', index)"
      @right="$emit('right', index)"
      @delete="$emit('delete', index)"
    />
  </span>
</template>

<style lang="scss" scoped>
.pera-image {
  position: relative;
  display: inline-block;
}

.thumbnail {
  display: inline-block;
  width: 270px;
  height: 270px;
}

</style>
