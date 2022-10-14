<template>
  <Header></Header>
  <h1>Hello User, Welcome to Update Restaurant Page</h1>
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
    <button type="button" @click="updateRestaurant">Update Restaurant</button>
  </form>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Update",
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
  async mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
    const res = await axios.get(
      `http://localhost:3000/restaurants/${this.$route.params.id}`
    );
    this.restaurant = res.data;
  },
  methods: {
    async updateRestaurant() {
      const res = await axios.put(
        `http://localhost:3000/restaurants/${this.$route.params.id}`,
        {
          name: this.restaurant.name,
          address: this.restaurant.address,
          contact: this.restaurant.contact,
        }
      );

      if (res.status === 200) {
        this.$router.push({ name: "Home" });
      }
    },
  },
};
</script>

<style></style>
