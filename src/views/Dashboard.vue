<template>
  <select v-model="selectedSeason">
    <option value="Spring" selected>Spring</option>
    <option value="Summer">Summer</option>
    <option value="Fall">Fall</option>
    <option value="Winter">Winter</option>
  </select>
  <Crops v-bind="componentProps" />
  <People v-bind="componentProps" />
  <ToDoList />
</template>
<script>
import ToDoList from "@/components/ToDoList.vue"
import Crops from "../components/Crops.vue"
import People from "../components/People.vue"
/**
 * @vue-data {String} selectedSeasons - Estación seleccionada
 * @vue-computed {Prop} componentProps - Devuelve el prop de la estación seleccionada
 */
export default {
  name: "Dashboard",
  components: {
    ToDoList,
    Crops,
    People,
  },
  data() {
    return {
      selectedSeason: "Spring",
    }
  },
  computed: {
    componentProps() {
      switch (this.selectedSeason) {
        case "Spring":
          return { season: "Spring" }
        case "Summer":
          return { season: "Summer" }
        case "Fall":
          return { season: "Fall" }
        case "Winter":
          return { season: "Winter" }
        default:
          return {}
      }
    },
  },
  mounted() {
    const selectedSeason = localStorage.getItem("selectedSeason")
    if (selectedSeason) {
      this.selectedSeason = selectedSeason
    }
  },
  watch: {
    selectedSeason(newVal) {
      localStorage.setItem("selectedSeason", newVal)
    },
  },
}
</script>
