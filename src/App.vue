<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <LoginComponent msg="Login"/>
</template>

<script>
import LoginComponent from './components/LoginComponent.vue'

export default {
  name: 'App',
  components: {
    LoginComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
