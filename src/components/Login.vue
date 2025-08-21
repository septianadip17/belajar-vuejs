<template>
  <img class="logo" src="/vite.svg" alt="logo">
  <h1>Login</h1>
  <div class="login">
    <input type="email" placeholder="Email" v-model="email" />
    <input type="password" placeholder="Password" v-model="password" />
    <button v-on:click="login">Login</button>
  </div>
  <p>Don't have an account? <router-link to="/sign-up">Sign Up</router-link></p>
</template>

<script>
export default {
  name: 'Login',
}
</script>

<style>

</style>