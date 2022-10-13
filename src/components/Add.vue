<template>
  <Header></Header>
  <h1>Hello User, Welcome to Add Restaurant Page</h1>
  <form class="add">
    <input
      v-model="restaurant.name"
      type="text"
      name="name"
      placeholder="Restaurant Name"
    />
    <input
      v-model="restaurant.address"
      type="text"
      name="address"
      placeholder="Address"
    />
    <input
      v-model="restaurant.contact"
      type="text"
      name="contact"
      placeholder="Contact"
    />
    <button type="button" @click="addRestaurant">Add Restaurant</button>
  </form>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Add",
  components: {
    Header,
  },
  data() {
    return {
      restaurant: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  methods: {
    async addRestaurant() {
      const res = await axios.post("http://localhost:3000/restaurants", {
        name: this.restaurant.name,
        address: this.restaurant.address,
        contact: this.restaurant.contact,
      });

      if (res.status === 201) {
        this.$router.push({ name: "Home" });
      }
      console.log(res, "res");
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>

<style></style>
