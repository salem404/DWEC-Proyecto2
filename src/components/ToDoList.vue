<script setup>
import { ref } from "vue"

const items = ref(["hello", "world", "a"])
</script>

<template>
  <ul>
    <li v-for="item in items">{{ item }}</li>
  </ul>
</template>
