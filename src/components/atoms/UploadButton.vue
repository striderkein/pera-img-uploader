<script setup>
defineProps({
  text: {
    type: String,
    required: false
  }
})

const handleClick = () => {
  // TODO: implement
  alert('保存ボタンが押されました')
}
</script>

<template>
  <button class="upload-button" @click="handleClick">{{ text }}</button>
</template>

<style scoped>
/*
.upload-button {
  opacity: 0.5;
  border: none;
  color: white;
  background-color: #999;
  border-radius: 3px;
  padding: 10px;
}
*/
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
