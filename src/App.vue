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
        <contact></contact>
      </div>
      <div class="col-md-6">
        <resize></resize>
      </div>
    </div>
  </div>
</template>

<script>
import Login from './components/Login.vue'
import Register from './components/Register.vue'
import Contact from './components/Contact.vue'
import Resize from './components/Resize_image.vue'
import Model from './components/Model.vue'

export default {
  name: 'app',
  components: {
    Login,
    Register,
    Contact,
    Resize,
    Model
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
