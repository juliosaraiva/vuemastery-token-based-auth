<template>
  <div>
    <form @submit.prevent="login">
      <label for="email">Email:</label>
      <input type="email" v-model="email" name="email" />

      <label for="password">Password:</label>
      <input type="password" v-model="password" name="password" />

      <button type="submit" name="button">Login</button>
      <router-link to="/register">Already have an account? Register.</router-link>
    </form>
  </div>
</template>

<script>
export default {
  name: 'LoginUser',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login() {
      this.$store
        .dispatch('login', {
          email: this.email,
          password: this.password
        })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
    }
  }
}
</script>

<style scoped>
button {
  cursor: pointer;
}
</style>