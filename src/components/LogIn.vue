<template>
  <img
    src="../assets/Restaurant-Logo-or-Icon-Design-Vector-Graphics-9987300-2-580x387.jpeg"
    class="logo"
  />
  <h1>Login</h1>
  <div class="login">
    <input v-model="email" type="text" placeholder="Email" />
    <input v-model="password" type="password" placeholder="Password" />
    <button @click="login">Login</button>
    <p><router-link to="/sign-up">Sign Up</router-link></p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "LogIn",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      let res = await axios.get(
        `http://localhost:3000/users?email=${this.email}&password=${this.password}`
      );

      if (res.status === 200 && res.data.length > 0) {
        this.$router.push({ name: "Home" });
        localStorage.setItem("user-info", JSON.stringify(res.data[0]));
      }
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>

<style></style>
