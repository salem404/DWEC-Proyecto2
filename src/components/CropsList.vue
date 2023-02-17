<script setup>
import { ref } from "vue"
import { reactive, computed } from "vue"

import json from "@/data/crops.json"
import Crop from "./Crop.vue"

const state = reactive({
  myArray: ["item1", "item2", "item3"],
})

const arrayLength = computed(() => {
  return state.myArray.length
})

const crops = json["crops"]

const seasons = ref(["Spring", "Summer", "Fall", "Winter"])
</script>
<template>
  <label>
    <input type="checkbox" value="Spring" v-model="seasons" />
    Spring
  </label>
  <label>
    <input type="checkbox" value="Summer" v-model="seasons" />
    Summer
  </label>
  <label>
    <input type="checkbox" value="Fall" v-model="seasons" />
    Fall
  </label>
  <label>
    <input type="checkbox" value="Winter" v-model="seasons" />
    Winter
  </label>
  {{ seasons }}
  <div>
    <ul v-for="data in crops">
      {{
        data
      }}
    </ul>
  </div>
</template>
