<script setup>
import { ref } from "vue";
import Login from "./Login.vue";
import Register from "./Register.vue";

const isLogged = ref(true);
const selected = ref("");
</script>
<template>
  <div class="access">
    <div v-if="isLogged" class="access__option">Welcome</div>
    <select v-else v-model="selected" class="access__option">
      <option value="">{{ selected ? "Return" : "Click me" }}</option>
      <option value="Login">Login</option>
      <option value="Register">Register</option>
    </select>
    <div v-if="selected === 'Login'">
      <Login />
    </div>
    <div v-else-if="selected === 'Register'">
      <Register />
    </div>
    <div v-else class="access__welcome">
      <div v-if="isLogged">
        <p>Username</p>
        <label>
          <input type="checkbox" v-model="isLogged" />
          Logged
        </label>
      </div>
      <div v-else>
        <p>Choose your access method</p>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
.access {
  max-width: 50%;
  box-sizing: border-box;
  background: rgba(217, 217, 217, 0.83);
  border: 28px solid var(--dark-blue);
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  border-radius: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-items: center;
  &__option {
    position: relative;
    top: -1em;
    margin-left: 1em;
    margin-right: 1em;
    padding: 0.1em;
    box-sizing: border-box;
    background: var(--blue);
    border: 7px solid #135c7d;
    border-radius: 14px;
    font-size: 4em;
    text-align: center;
    color: var(--white);
  }
  &__welcome {
    position: relative;
    top: -1em;
    margin-block-start: 0;
    margin-block-end: 0;
    font-style: normal;
    font-weight: 400;
    font-size: 2em;
    line-height: 44px;
    color: var(--black);
  }
}
//Mobile
@media only screen and (max-width: 768px) {
}
</style>
