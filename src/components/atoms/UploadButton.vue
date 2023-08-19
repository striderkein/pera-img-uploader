<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['click'])

defineProps({
  text: {
    type: String,
    required: false
  }
})

const handleClick = () => {
  emit('click')
}
</script>

<template>
  <button
    class="upload-button"
    @click="handleClick"
  >{{ text }}</button>
</template>

<style scoped>
.upload-button {
  /* TODO: implement some style on your favor */
  width: 100%;
  border: none;
  color: white;
  background-color: #03D5AC; /* spoited */
  border-radius: 3px;
  padding: 10px;
}

</style>
