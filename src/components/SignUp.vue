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
  </div>
</template>

<script>
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
    signUp() {
      console.log(this.name, this.email, this.password);
    },
  },
};
</script>

<style>
.logo {
  width: 150px;
}
.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
  border: 1px solid skyblue;
}

.register button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  background-color: skyblue;
  color: white;
  cursor: pointer;
}
</style>
