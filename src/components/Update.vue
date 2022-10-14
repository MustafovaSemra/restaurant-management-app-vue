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
    <button type="button" @click="addRestaurant">Update Restaurant</button>
  </form>
</template>

<script>
import Header from "./Header.vue";

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
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>

<style></style>
