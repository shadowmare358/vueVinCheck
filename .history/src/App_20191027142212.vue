<template>
  <div id="app">
    <search></search>
  </div>
</template>

<script>
import Search from './components/Search.vue'

export default {
  name: 'app',
  components: {
    Search
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
  width: 100vw;
  height: 100vh;
  background-size: cover;

}
#app:after{
   content: "";
 background-image: url("./img/car.png");
 background-size: cover;
  opacity: 0.5;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
}

</style>
