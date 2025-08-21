<template>
  <img class="logo" src="../assets/vue.svg" alt="logo">
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" name="username" v-model="name" placeholder="Enter Name">
    <input type="email" name="email" v-model="email" placeholder="Enter Email">
    <input type="password" name="password" v-model="password" placeholder="Enter Password">
    <button v-on:click="signUp">Sign Up</button>
  </div>
</template>

<script>
export default {
  name: 'SignUp',
  data() {
    return {
      name: '',
      email: '',
      password: ''
    };
  },
  methods: {
    signUp() {
      // Logic for signing up the user
      console.log('User signed up:', this.name, this.email, this.password);
      // Reset fields after sign up
      this.name = '';
      this.email = '';
      this.password = '';
    }
  },
}
</script>

<style>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid skyblue;
}

.register button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background: skyblue;
  color: white;
  cursor: pointer;
}
</style>