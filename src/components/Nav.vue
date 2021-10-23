<template>
  <nav class="navbar navbar-expand navbar-light fixed-top">
    <div class="container">
      <router-link to="/" class="navbar-brand">Home</router-link>
      <div class="collapse navbar-collapse">
        <ul class="navbar-nav ml-auto" v-if="!user">
          <li class="nav-item"><router-link to="Login" class="nav-link">Login</router-link></li>
          <li class="nav-item"><router-link to="Register" class="nav-link">Signup</router-link></li>
        </ul>

        <ul class="navbar-nav ml-auto" v-if="user">
          <li class="nav-item"><router-link to="Login" class="nav-link">Logout</router-link></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Nav',
  data() {
    return {
      user: ''
    }
  },
  async created() {
    const response = await axios.get('user');

    if (response.data.id != '') {
      this.user = response.data;
    }
  }
}
</script>

<style scoped>

</style>