<template>
  <div class="container">
    <div>
      <h1 class="title">
        nuxt-github-oauth-example
      </h1>
      <h2 class="subtitle">
        This is an example of implementing oauth with nuxtjs and github
      </h2>
      <div>
        <nuxt-link to="/secret">Go to secret page</nuxt-link>
      </div>
      <div>
        <span>user</span><span>{{ user }}</span>
      </div>
      <div>
        <button v-if="!loggedIn" type="button" @click="login">
          Login with github
        </button>
        <button v-if="loggedIn" type="button" @click="logout">
          Logout
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loggedIn: this.$auth.loggedIn,
      user: this.$auth.user
    }
  },
  methods: {
    login() {
      this.$auth.loginWith('github')
    },
    logout() {
      this.$auth.logout()
      window.location.reload(true)
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
button {
  font-size: 20px;
}
</style>
