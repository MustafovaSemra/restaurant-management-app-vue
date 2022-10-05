<template>
  <h1>Hello User, Welcome to Home Page</h1>
  <Header></Header>
</template>

<script>
import Header from "./Header.vue";

export default {
  name: "HomePage",
  components: {
    Header,
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
