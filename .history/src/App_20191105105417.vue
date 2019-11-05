<template>
  <div id="app">
    <search></search>
     <div id="car"></div>
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
  background-size: cover;

}
body{
   content: "";
 background-size: cover;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
}
#car{
  position: absolute;
  top: 50%;
  left: 50%;
  transform:translate(-50%,-50%);
  width: 800px;
  height: 600px;
  background-image: url('./img/whiteporsche.gif');
  opacity: 0.5;
  z-index: -1;
}

</style>
