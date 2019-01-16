<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <div id="app2">
    <mynavbar></mynavbar>
    <!-- <router-view></router-view> -->
  </div>
    <router-view/>
  </div>
</template>

<script>
import mynavbar from './components/AppComponents/Navbar.vue'

export default {
  name: 'app2',
  components: {
    mynavbar
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
  margin-top: 0px;
}
</style>
