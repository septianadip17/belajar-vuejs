<template>
  <img class="logo" src="../assets/vue.svg" alt="logo">
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" name="username" v-model="name" placeholder="Enter Name">
    <input type="email" name="email" v-model="email" placeholder="Enter Email">
    <input type="password" name="password" v-model="password" placeholder="Enter Password">
    <button v-on:click="signUp">Sign Up</button>
    <p>Already have an account?</p>
    <p>Click here to <router-link to="/login">Login</router-link></p>
  </div>
</template>

<script>
import axios from 'axios';
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
    async signUp() {
      let result = await axios.post('http://localhost:3000/users', {
        name: this.name,
        email: this.email,
        password: this.password
      });
      console.log(result);
      if (result.status === 201) {
        localStorage.setItem('user-info', JSON.stringify(result.data));
        this.$router.push({ name: 'Home' });
      } else {
        alert('Failed to register user.');
      }
    }
  },
  mounted() {
    let user = localStorage.getItem('user-info');
    if (user) {
      this.$router.push({ name: 'Home' });
    }
  }
}
</script>

<style>

</style>