<template>
  <div>
    <h1>Things to do</h1>
    <form @submit.prevent="addTarea">
      <input v-model="newTarea" required />
      <button>Add</button>
    </form>
    <ul v-if="!isEmpty">
      <li v-for="(tarea, index) in tareas" :key="index">
        <input
          v-if="!tarea.done"
          type="checkbox"
          v-model="tarea.done"
          @change="saveTarea(index)"
        />
        <span :class="{ done: tarea.done }">{{ tarea.nombre }}</span>
        <button v-if="tarea.done" @click="deleteTarea(index)">Delete</button>
      </li>
    </ul>
    <p v-else>You made it!</p>
  </div>
</template>
<script>
/**
 * @vue-data {Array} [tareas=[]] - Lista de tareas
 * @vue-data {String} [newTarea=""] - Tarea nueva a añadir
 * @vue-data {Boolean} [isEmpty=true] - Estado de la lista de tareas
 * @vue-event {Array} fetchTareas - Llama a la api para adquirir la lista de tareas
 * @vue-event {Array} saveTarea - Llama a la api para guardar una tarea existente
 * @vue-event {Array} addTarea - Llama a la api para añador una tarea nueva
 * @vue-event {Array} deleteTarea - Llama a la api para eliminar una tarea
 */
export default {
  name: "ToDoList",
  data() {
    return {
      tareas: [],
      newTarea: "",
      isEmpty: true,
    }
  },
  async mounted() {
    await this.fetchTareas()
  },
  methods: {
    async fetchTareas() {
      const response = await fetch("http://localhost:3001/api/tareas", {
        method: "GET",
        headers: { Connection: "Keep-Alive" },
      })
      if (response.ok) {
        const data = await response.json()
        this.tareas = data
        this.isEmpty = false
      } else {
        this.isEmpty = true
      }
    },
    async saveTarea(index) {
      const tarea = {
        nombre: this.tareas[index].nombre,
        done: this.tareas[index].done,
      }
      console.log(tarea)
      const response = await fetch(
        `http://localhost:3001/api/tareas/${tarea.nombre}`,
        {
          method: "PUT",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(tarea),
        }
      )
      const data = await response.json()
      this.tareas[index].editing = false
    },
    async addTarea() {
      this.tareas = []
      if (this.newTarea) {
        const tarea = {
          nombre: this.newTarea,
          done: "false",
        }
        const response = await fetch("http://localhost:3001/api/tareas", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(tarea),
        })
        const data = await response.json()
        this.fetchTareas()
        this.newtarea = ""
      }
    },
    async deleteTarea(index) {
      const tarea = this.tareas[index]
      const response = await fetch(
        `http://localhost:3001/api/tareas/${tarea.nombre}`,
        {
          method: "DELETE",
          headers: {
            "Content-Type": "application/json",
          },
        }
      )
      if (response.ok) {
        this.fetchTareas()
      }
    },
  },
}
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>
