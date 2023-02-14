<template>
  <form>
    <div class="container">
      <label for="username"><b>Username</b></label>
      <input
        type="text"
        placeholder="Enter Username"
        name="username"
        required
      />

      <label for="psw"><b>Password</b></label>
      <input type="password" placeholder="Enter Password" name="psw" required />

      <button type="submit">Login</button>
      <label> <input type="checkbox" name="remember" /> Remember me </label>
    </div>
  </form>
</template>

<style lang="scss" scoped>
form {
  div {
    display: flex;
    flex-direction: column;
    margin: 10px 5px;

    p {
      margin: 0px;
    }
  }
  label {
    color: var(--color);
  }
  input,
  select {
    font-size: 1rem;
    padding: 5px;
  }
}
</style>
