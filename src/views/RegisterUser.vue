<template>
  <div>
    <form @submit.prevent="register">
      <label for="name">
        Name:
      </label>
      <input v-model="name" name="name" type="text">
      <label for="email">
        Email
      </label>
      <input v-model="email" name="email" type="email">
      <label for="password">
        Password
      </label>
      <input v-model="password" name="password" type="password">
      <button type="submit" name="button">
        Register
      </button>

      <ul>
        <li v-for="(error, idx) in errors" :key="idx">
          {{ error }}
        </li>
      </ul>
    </form>

    <router-link to="/login">
      Already have an account? Login.
    </router-link>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      email: '',
      password: '',
      errors: null
    }
  },
  methods: {
    register () {
      this.$store.dispatch('register', {
        name: this.name,
        email: this.email,
        password: this.password
      })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
        .catch(err => {
          this.errors = err.response.data.errors
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
