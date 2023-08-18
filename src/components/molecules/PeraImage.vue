<script setup>
import SquareImage from '@/components/atoms/SquareImage.vue'
import EditButton from '@/components/atoms/EditButton.vue'

defineProps({
  image: {
    type: Object,
    required: true
  }
})
</script>

<template>
  <span class="pera-image">
    <square-image class="thumbnail" :image="image" />
    <edit-button class="edit-button"/>
  </span>
</template>

<style scoped>
/* implement some style on your favor */
.pera-image {
  position: relative;
  display: inline-block;
  /* justify-content: center; */
  /* align-items: center; */
  /* height: 100%; */
}

.thumbnail {
  display: inline-block;
  width: 270px;
  height: 270px;
}

.edit-button {
  position: absolute;
  top: 10px;
  right: 10px;
}
</style>
