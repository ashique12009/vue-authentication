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
          <li class="nav-item"><a href="javascript:void(0)" class="nav-link" @click="handleLogout">Logout</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
  name: 'Nav',
  methods: {
    handleLogout() {
      localStorage.removeItem('token');

      // Store null to user to vuex store
      this.$store.dispatch('user', null);
      
      this.$router.push('/login');
    }
  },
  computed: {
    ...mapGetters(['user'])
  }
}
</script>

<style scoped>

</style>