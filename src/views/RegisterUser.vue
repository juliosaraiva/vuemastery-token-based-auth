<template>
  <div>
    <form @submit.prevent="register">
      <label for="name">Name:</label>
      <input v-model="name" name="name" type="text" />
      <label for="email">Email:</label>
      <input v-model="email" name="email" type="email" />
      <label for="password">Password:</label>
      <input v-model="password" name="password" type="password" />
      <button type="submit" name="button">Register</button>
      <router-link to="/login">Already have an account? Login.</router-link>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      password: ''
    }
  },
  methods: {
    register() {
      this.$store
        .dispatch('register', {
          name: this.name,
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