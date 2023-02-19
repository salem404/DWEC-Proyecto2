<template>
  <div>
    <h2>Crops</h2>
    <ul>
      <li v-for="crop in crops">
        <p v-if="crop.seasons.includes(season)">
          {{ crop.name }}
        </p>
      </li>
    </ul>
  </div>
</template>
<script>
/**
 * @vue-prop {String} season - Estación seleccionada
 * @vue-data {Array} [crops = []] - Lista de personas
 * @vue-event {Array} fetchCrops - Llama a la api para adquirir la lista de cultivos
 */
export default {
  name: "Crops",
  props: {
    season: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      crops: [],
    }
  },
  async mounted() {
    await this.fetchCrops()
  },
  methods: {
    async fetchCrops() {
      const response = await fetch("http://localhost:3001/api/crops", {
        method: "GET",
        headers: { Connection: "Keep-Alive" },
      })
      if (response.ok) {
        const data = await response.json()
        this.crops = data
      }
    },
  },
}
</script>
