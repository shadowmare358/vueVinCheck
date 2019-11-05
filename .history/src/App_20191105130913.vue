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
  color:rgb(63, 7, 7);
  margin-top: 60px;
  background-size: cover;

}
body{
margin: 0;
padding: 0;
height: 100%;
background-color: #FFE8AC;
}
#car{
  position: absolute;
  top: 90%;
  left: 50%;
  transform:translate(-50%,-50%);
  width: 800px;
  height: 600px;
  background-image: url('./img/car.gif');
  z-index: -1;
}
@media (max-width: 700px){
  #car{
    width: 300px;
    height: 500px;
    right: 0;
    top: 50%;
  }
}
</style>
