<template>
  <div id="app">
    <search></search>
     <div id="car"></div>
  </div>

</template>

<script>
import Search from './components/Search.vue'
import dotenv from 'dotenv';
dotenv.con
export default {
  name: 'app',
  components: {
    Search
  }
}

</script>

<style>
*{
  margin: 0;
  padding: 0;
}
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
background-color: #FFE8AC;
}
#car{
  position: absolute;
  top: 70%;
  left: 50%;
  transform:translate(-50%,-50%);
  opacity: 0.5;
  width: 800px;
  height: 600px;
  background-image: url('./img/car.gif');
  z-index: -1;
}
@media (max-width: 800px){
  *{
    overflow-x: hidden;
  }
  #car{
display: none;
  }
  body{
     background: linear-gradient(rgba(255,255,255,.6), rgba(255,255,255,.6)), url('./img/car2.svg');
    background-repeat: no-repeat;
     background-attachment: fixed;
  background-position: center;
  }
}
</style>
