<script setup>
import { ref } from "vue"
import ToDo from "./ToDo.vue"
import json from "@/data/toDos.json"
const toDos = json["toDos"]

const newToDo = ref("")
</script>
<template>
  <div>
    <h1>Tareas</h1>
    <input v-model="newToDo" type="text" />
    <div v-for="data in toDos">
      <ul>
        <li>
          {{ data.description }}
          <input type="checkbox" v-model="data.done" />
        </li>
      </ul>
    </div>
  </div>
</template>
