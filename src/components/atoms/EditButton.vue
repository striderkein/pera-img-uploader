<script setup>
import { defineProps, ref } from 'vue';
import IconTrashCan from '@/components/icons/IconTrashCan.vue'

const isExpand = ref(false);

const emit = defineEmits(['delete']);

defineProps({
  index: {
    type: Number,
    required: true
  }
})

function handleSettingClick() {
  isExpand.value = true;
  console.log(`isExpand: ${isExpand.value}`)
}

const handleEditClick = (operation, index) => {
  isExpand.value = false;
  console.log(`isExpand: ${isExpand.value}`)

  if (operation === 'left') {
    console.log('左へ移動するよ')
  } else if (operation === 'right') {
    console.log('右へ移動するよ')
  } else if (operation === 'delete') {
    emit('delete', index)
  } else {
    console.log('なんかおかしいよ')
  }
}
</script>

<template>
  <button v-show="!isExpand" class="edit-button" @click="handleSettingClick">設定</button>
  <span v-show="isExpand" class="edit-button expand">
    <ul>
      <li @click="handleEditClick('left')"><span class="icon">←</span>左へ移動</li>
      <li @click="handleEditClick('right')"><span class="icon">→</span>右へ移動</li>
      <li @click="handleEditClick('delete', index)" class="delete"><span class="icon"><icon-trash-can /></span>画像を削除</li>
    </ul>
  </span>
</template>

<style scoped>
.edit-button {
  opacity: 0.5;
  border: none;
  color: white;
  background-color: #999;
  border-radius: 3px;
  padding: 10px;
  /* copy from parent */
  position: absolute;
  top: 10px;
  right: 10px;
}

.edit-button.expand {
  color: #333;
  opacity: unset;
  background-color: #fff;
}

.edit-button.expand ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.edit-button.expand ul li:not(:last-child) {
  border-bottom: 1px solid #000;
}

li.delete {
  color: #F00;
}

.icon {
  margin-right: 5px;
}
</style>
