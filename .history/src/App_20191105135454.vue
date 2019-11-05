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
  top: 80%;
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
  body::after{
  content: "";
  background: url('./img/car2.svg');
  opacity: 0.5;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  position: absolute;
  z-index: -1;
  background-image:
  }
}
</style>
