<template>
  <div class="auth-inner">
    <form @submit.prevent="handleLoginSubmit">
      <div class="form-group">
        <label>Email</label>
        <input type="email" class="form-control" v-model="email" placeholder="Email" />
      </div>
      <div class="form-group">
        <label>Password</label>
        <input type="password" class="form-control" v-model="password" placeholder="Password" />
      </div>
      <button class="btn btn-primary">Login</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Login',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async handleLoginSubmit() {
      const response = await axios.post('login', {
        email: this.email,
        password: this.password
      });

      if (response.data.token != '') {
        localStorage.setItem('token', response.data.token);
        
        // Store user to store
        this.$store.dispatch('user', response.data.user);

        // Now redirect to profile page
        this.$router.push('/profile');
      }
    }
  }
}
</script>