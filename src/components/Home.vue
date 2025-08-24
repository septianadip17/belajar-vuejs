<template>
  <Header />
  <h1>Hello {{ name }}, Welcome to Home</h1>
  <table border="1">
    <tr>
      <th>ID</th>
      <th>Name</th>
      <th>Contact</th>
      <th>Address</th>
      <th>Actions</th>
    </tr>
    <tr v-for="item in restaurants" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.contact }}</td>
      <td>{{ item.address }}</td>
      <td style="display: flex; gap: 10px; justify-content: center; align-items: center">
        <router-link :to="'/update/' + item.id">Update</router-link>
        <button v-on:click="deleteRestaurant(item.id)">Delete</button>
      </td>
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
  methods: {
    async deleteRestaurant(id) {
      let result = await axios.delete('http://localhost:3000/restaurants/' + id);
      if (result.status === 200) {
        this.loadData();
      }
    },
    async loadData() {
      let user = localStorage.getItem('user-info');
      this.name = JSON.parse(user).name;
      if (!user) {
        this.$router.push({ name: 'SignUp' });
      }
      let result = await axios.get('http://localhost:3000/restaurants');
      console.warn(result);
      this.restaurants = result.data;
    }
  },
  async mounted() {
    this.loadData();
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