<template>
  <div>
    <h2>People</h2>
    <ul>
      <li v-for="person in people">
        <p v-if="person.birthday.season == season">
          {{ person.name }}
          {{ person.birthday.day }}
        </p>
      </li>
    </ul>
  </div>
</template>
<script>
/**
 * @vue-prop {String} season - Estación seleccionada
 * @vue-data {Array} [people = []] - Lista de personas
 * @vue-event {Array} fetchPeople - Llama a la api para adquirir la lista de personas
 */
export default {
  name: "People",
  props: {
    season: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      people: [],
    }
  },
  async mounted() {
    await this.fetchPeople()
  },
  methods: {
    async fetchPeople() {
      const response = await fetch("http://localhost:3001/api/people", {
        method: "GET",
        headers: { Connection: "Keep-Alive" },
      })
      if (response.ok) {
        const data = await response.json()
        this.people = data
      }
    },
  },
}
</script>
