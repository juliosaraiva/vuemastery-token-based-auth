<template>
  <div>
    <form @submit.prevent="login">
      <label for="email">
        Email
      </label>
      <input v-model="email" type="email" name="email">
      <label for="password">
        Password
      </label>
      <input v-model="password" type="password" name="password">
      <button type="submit" name="button">
        Login
      </button>
      <p>{{ error }}</p>
    </form>
    <router-link to="/register">
      Already have an account? Register.
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'LoginUser',
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    login () {
      this.$store.dispatch('login', {
        email: this.email,
        password: this.password
      }).then(() => {
        this.$router.push({ name: 'dashboard' })
      }).catch(err => {
        this.error = err.response.data.error
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
