<template>
  <div class="nav">
    <a @click="logout" href="#">Log Out</a>
    <router-link to="/add">Add Restaurant</router-link>
    <router-link to="/">Home</router-link>
  </div>
</template>

<script>
export default {
  name: "Header",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "LogIn" });
    },
  },
};
</script>

<style>
.nav {
  background-color: black;
  overflow: hidden;
}

.nav a {
  float: right;
  color: white;
  padding: 14px 16px;
  text-align: center;
  font-size: 17px;
  text-decoration: none;
  margin-right: 5px;
}

.nav a:hover {
  background-color: #ddd;
  color: #333;
}
</style>
