<template>
  <Header></Header>
  <h1>Hello {{ name }}, Welcome to Home Page</h1>
  <table border="1">
    <tr>
      <td>ID</td>
      <td>Name</td>
      <td>Contact</td>
      <td>Address</td>
      <td>Actions</td>
    </tr>
    <tr v-for="item in restaurants" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.contact }}</td>
      <td>{{ item.address }}</td>
      <td><router-link :to="`/update/${item.id}`">Update</router-link></td>
    </tr>
  </table>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Header,
  },
  data() {
    return {
      name: "",
      restaurants: [],
    };
  },
  async mounted() {
    let user = localStorage.getItem("user-info");
    this.name = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }

    let res = await axios.get("http://localhost:3000/restaurants");

    this.restaurants = res.data;
  },
};
</script>

<style>
td {
  width: 160px;
  height: 40px;
}
</style>
