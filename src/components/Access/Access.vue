<script setup>
import { ref } from "vue"
import Login from "./Login.vue"
import Register from "./Register.vue"

const isLogged = true
const selected = ref("")
</script>
<template>
  <div v-if="isLogged">
    <select v-model="selected">
      <option value="">{{ selected ? "Volver" : "Púlsame" }}</option>
      <option value="Login">Login</option>
      <option value="Register">Register</option>
    </select>
    <div v-if="selected === 'Login'">
      <Login />
    </div>
    <div v-else-if="selected === 'Register'">
      <Register />
    </div>
    <div v-else>Elige tu método de acceso</div>
  </div>
  <div v-else>a</div>
</template>
