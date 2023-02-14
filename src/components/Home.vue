<script setup>
import Login from "./Access/Access.vue"
</script>

<template>
  <main class="home">
    <h1 class="home__heading">Coral Companion</h1>
    <Login />
  </main>
</template>

<style lang="scss" scoped>
.home {
  height: 100%;
  display: grid;
  grid-template-columns: 1.1fr 0.9fr;
  grid-template-rows: 100%;
  background-color: var(--blue);
  gap: 0px 0px;
  &__heading {
    margin: 0;
  }
}
</style>
