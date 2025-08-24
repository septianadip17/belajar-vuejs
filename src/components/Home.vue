<template>
  <Header />
  <h1>Hello {{ name }}, Welcome to Home</h1>
  <table border="1">
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Contact</th>
      <th>Address</th>
    </tr>
    <tr v-for="item in restaurants" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.contact }}</td>
      <td>{{ item.address }}</td>
    </tr>
  </table>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
  name: 'Home',
  data() {
    return {
      name: '',
      restaurants: []
    };
  },
  components: {
    Header
  },
  async mounted() {
    let user = localStorage.getItem('user-info');
    this.name = JSON.parse(user).name;
    console.log(this.name);
    console.log(user);
    if (!user) {
      this.$router.push({ name: 'SignUp' });
    }
    let result = await axios.get('http://localhost:3000/restaurants');
    console.warn(result);
    this.restaurants = result.data;
  }
};
</script>

<style>
table {
  margin: auto;
}
td {
  width: 160px;
  height: 40px;
}
</style>