<template>
  <div class="auth-inner">
    <form>
      <div class="form-group">
        <label>Email</label>
        <input type="email" class="form-control" placeholder="Email" />
      </div>
      <div class="form-group">
        <label>Password</label>
        <input type="password" class="form-control" placeholder="Password" />
      </div>
      <button class="btn btn-primary">Login</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Login'
}
</script>