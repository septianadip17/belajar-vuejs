<template>
  <div class="nav">
    <a href="#">Home</a>
    <a href="#">Add Restaurant</a>
    <a href="#">Update Restaurant</a>
    <a v-on:click="logout" href="#">Logout</a>
  </div>
</template>

<script>
export default {
  name: 'Header',
  methods: {
    logout() {
      console.log('Logging out');  
      localStorage.clear();
      this.$router.push({ name: 'Login' });
    }
  }
};
</script>

<style>
.nav {
  background-color: #333;
  padding: 10px;
  overflow: hidden;
}

.nav a {
  float: left;
  color: #f2f2f2;
  padding: 14px 16px;
  text-decoration: none;
  text-align: center;
  font-size: 17px;
  margin-right: 5px;
}

.nav a:hover {
  background: #ddd;
  color: black;
}
</style>