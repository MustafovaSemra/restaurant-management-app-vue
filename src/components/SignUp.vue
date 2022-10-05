<template>
  <img
    src="../assets/Restaurant-Logo-or-Icon-Design-Vector-Graphics-9987300-2-580x387.jpeg"
    class="logo"
  />
  <h1>Sign Up</h1>
  <div class="register">
    <input v-model="name" type="text" placeholder="Name" />
    <input v-model="email" type="text" placeholder="Email" />
    <input v-model="password" type="password" placeholder="Password" />
    <button @click="signUp">Sign Up</button>
    <p><router-link to="/login">Login</router-link></p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SignUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      let res = await axios.post("http://localhost:3000/users", {
        email: this.email,
        password: this.password,
        name: this.name,
      });

      if (res.status === 201) {
        this.$router.push({ name: "Home" });
        localStorage.setItem("user-info", JSON.stringify(res.data));
      }

      console.log(res, "res");
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
