<script setup>
const item = defineProps(["prp"])
item.editing = false
const editItem = (index) => {}
const saveItem = (index) => {}
const cancelEdit = (index) => {}
</script>
<template>
  <div v-if="!item.editing">
    {{ item.text }}
    <button @click="editItem(index)">Edit</button>
    <button @click="deleteItem(index)">Delete</button>
  </div>
  <div v-else>
    <input v-model="item.text" />
    <button @click="saveItem(index)">Save</button>
    <button @click="cancelEdit(index)">Cancel</button>
  </div>
</template>
