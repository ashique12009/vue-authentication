<template>
  <div class="auth-inner">
    <h3 v-if="user">Hi, {{ user.first_name }} {{ user.last_name }}</h3>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Profile',
  data() {
    return {
      user: null
    }
  },
  async created() {
    const response = await axios.get('user');

    if (response.data.id != '') {
      this.user = response.data;
    }
    else {
      this.$router.push('/login');
    }
  }
}
</script>

<style>

</style>