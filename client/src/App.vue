<template>
  <div id="app">
    <div id="nav">
      <n-navbar/>
      <n-login/>
      <n-register/>
    </div>
    <router-view/>
    <n-footer/>
  </div>
</template>

<script>
import nLogin from './components/n-login'
import navbarVue from './components/n-navbar'
import nRegister from './components/n-register'
import nFooter from './components/n-footer'
export default {
  name: 'App',
  components: {
    'n-navbar': navbarVue,
    'n-login': nLogin,
    'n-register': nRegister,
    nFooter
  },
  created () {
    if (localStorage.getItem('token') && localStorage.getItem('name')) {
      this.$store.commit('setIsLogin', true)
      this.$store.commit('setCurrentUser')
    }
    this.$store.dispatch('fetchQuestions')
  }
}
</script>
<style>
@import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap');

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

/* #nav {
  padding: 30px;
} */

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
