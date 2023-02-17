<template>
  <form>
    <div class="container">
      <label for="username"><b>Username</b></label>
      <input type="text" placeholder="Enter Username" name="username" required />

      <label for="psw"><b>Password</b></label>
      <input type="password" placeholder="Enter Password" name="psw" required />

      <button type="submit">Login</button>
    </div>
  </form>
</template>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 14px 45px 10px;
  gap: 45px;
  isolation: isolate;
  label {
    font-size: 36px;
    line-height: 44px;
  }
  button {
    /* Submit */

    width: 262px;
    height: 65px;

    /* Light/Blue Green */

    background: #0892b6;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 35px;
  }
}
</style>
