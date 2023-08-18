<script setup>
const handleClick = () => {
  // TODO: implement
  alert('編集ボタンが押されました')
}
</script>

<template>
  <button class="edit-button" @click="handleClick">設定</button>
</template>

<style scoped>
.edit-button {
  opacity: 0.5;
  border: none;
  color: white;
  background-color: #999;
  border-radius: 3px;
  padding: 10px;
}
</style>
