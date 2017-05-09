<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div class="container">
      <div class="col-md-6">
        <login></login>
      </div>
      <div class="col-md-6">
        <register></register>
      </div>
      <div class="col-md-6">
      </div>
    </div>
  </div>
</template>

<script>
import Login from './components/Login.vue'
import Register from './components/Register.vue'

export default {
  name: 'app',
  components: {
    Login,
    Register
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
