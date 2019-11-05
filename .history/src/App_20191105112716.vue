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
margin: 0;
padding: 0;
overflow: hidden;
background-color: #F5F5F5;
}
#car{
  position: absolute;
  top: 90%;
  left: 50%;
  transform:translate(-50%,-50%);
  width: 800px;
  height: 600px;
  background-image: url('./img/whiteporsche.gif');
  opacity: 0.5;
  z-index: -1;
}

</style>
