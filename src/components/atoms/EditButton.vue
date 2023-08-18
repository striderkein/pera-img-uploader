<script setup>
const handleClick = () => {
  // TODO: implement
  alert('編集ボタンが押されました')
}
</script>

<template>
	<!--
  <span class="edit-button">
    <button @click="handleClick">設定</button>
  </span>
  -->
  <!-- <span class="edit-button" @click="handleClick">設定</span> -->
  <button class="edit-button" @click="handleClick">設定</button>
</template>

<style scoped>
/* .edit-button > button { */
.edit-button {
  opacity: 0.5;
  border: none;
  color: white;
  background-color: #999;
  border-radius: 3px;
  padding: 10px;
}
</style>
