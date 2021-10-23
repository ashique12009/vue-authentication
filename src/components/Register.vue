<template>
  <div class="auth-inner">
    <form @submit.prevent="handleRegisterSubmit">
      <div class="form-group">
        <label>First Name</label>
        <input type="text" class="form-control" v-model="first_name" placeholder="First Name" />
      </div>
      <div class="form-group">
        <label>Last Name</label>
        <input type="text" class="form-control" v-model="last_name" placeholder="Last Name" />
      </div>
      <div class="form-group">
        <label>Email</label>
        <input type="email" class="form-control" v-model="email" placeholder="Email" />
      </div>
      <div class="form-group">
        <label>Password</label>
        <input type="password" class="form-control" v-model="password" placeholder="Password" />
      </div>
      <div class="form-group">
        <label>Confirm Password</label>
        <input type="password" class="form-control" v-model="password_confirm" placeholder="Confirm Password" />
      </div>
      <button class="btn btn-primary">Sign Up</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Register',
  data() {
    return {
      first_name: '',
      last_name: '',
      email: '',
      password: '',
      password_confirm: '',
    }
  },
  methods: {
    async handleRegisterSubmit() {
      const registerData = {
        first_name: this.first_name,
        last_name: this.last_name,
        email: this.email,
        password: this.password,
        password_confirm: this.password_confirm,
      }
      
      await axios.post('register', registerData);

      this.$router.push('/login');
    }
  }
}
</script>

<style scoped>
  .auth-inner{
    margin-top: 70px;
  }
</style>