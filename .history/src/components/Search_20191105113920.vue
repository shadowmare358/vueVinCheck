<template>
  <div class="search">
    <h1>CAR INFO PAGE</h1>
    <nav>
    <button class="btn-one" v-on:click="getPopularCarResults()">Show Ten Best Sellers In US</button>
    <button class="btn-one" v-on:click="getVIN()">Decode VIN</button>
    <input v-model="vin" v-on:keyup.enter="getVIN()">
    </nav>
    <div v-if="!carResults"></div>
    <ul v-if="showCarResults">
        <li v-for="result in carResults" v-bind:key="result.id">{{result.make}} {{result.model}} Number of cars sold: {{result.count}}</li>
    </ul>
<div v-if="showVinResults">
    <p>Year {{vinResults.year}}</p>
    <p>Brand {{vinResults.make}}</p>
    <p>Model {{vinResults.model}}</p>
    <p>Engine {{vinResults.engine}}</p>
    <p>Drive train {{vinResults.drivetrain}}</p>
    <p>Transmission {{vinResults.transmission}}</p>
    <p>Cylinders {{vinResults.cylinders}}</p>
</div>

  </div>
</template>

<script>
export default {
  name: "search",
  data() {
    return {
      msg: "Search",
      query: "",
      carResults: "",
      imagesResults: [],
      vinResults: [],
      modelInfo: "",
      vin: "",
      showCarResults: false,
      showVinResults: false
    };
  },
  methods: {
    async getPopularCarResults() {
        const marketApiKey = "NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu"
      await fetch(
        `https://marketcheck-prod.apigee.net/v1/popular/cars?api_key=${marketApiKey}&car_type=new`
      )
        .then(response => response.json())
        .then(myJson => this.carResults = myJson.slice(0,10))
        .catch(err => alert(`Cannot get requested data ${err}`));
        this.showVinResults=false;
        this.showCarResults=true;
    },
    async getImageResults(){
         const cxKey = '001912728085642910227:akqkacx3uim';
         const googleApiKey = 'AIzaSyCAJ2rKXL-X_daAy2dveCO--E5ciLgIK6k';
        const carResult = this.carResults[0];

       await fetch(
        `https://www.googleapis.com/customsearch/v1?q=${carResult}&key=${googleApiKey}&cx=${cxKey}&searchType=image&fileType=jpg&imgSize=small&alt=json`
      )
        .then(response => response.json())
        .then(myJson => this.imagesResults = myJson.items)
        .catch(err => alert(`Cannot get requested data ${err}`));
  },
  async getVIN(){
     await fetch(
        `http://marketcheck-prod.apigee.net/v1/vin/${this.vin}/specs?api_key=NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu`,{
          method: 'GET',
          host: "marketcheck-prod.apigee.net",
          headers:{
            "Content-type": "application/json",
            "Return-type": "Build"
          }
        }
      )
        .then(response => response.json())
        .then(myJson => JSON.stringify(this.vinResults = myJson))
        .catch(err => alert(`Cannot get requested data ${err}`));
        this.showCarResults=false;
        this.showVinResults=true;
  }
}
};
</script>
<style  scoped>
@import url('https://fonts.googleapis.com/css?family=Righteous&display=swap');
*{
    font-family: 'Open Sans Condensed', sans-serif;
}
.btn-one {

  font-size: 20px;
  font-weight: bold;
  line-height: 50px;
    height: 50px;
    text-align: center;
    width: 200px;
    cursor: pointer;
    color: white;
    transition: all 0.3s;
    position: relative;
    margin: 10px;
    background-color: darkslategray;
}
.btn-one span {
    transition: all 0.3s;
}
.btn-one::before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    opacity: 0;
    transition: all 0.3s;
    border-top-width: 1px;
    border-bottom-width: 1px;
    border-top-style: solid;
    border-bottom-style: solid;
    border-top-color: rgba(255,255,255,0.5);
    border-bottom-color: rgba(255,255,255,0.5);
    transform: scale(0.1, 1);
}
.btn-one:hover span {
    letter-spacing: 2px;
}
.btn-one:hover::before {
    opacity: 1;
    transform: scale(1, 1);
}
.btn-one::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    transition: all 0.3s;
    background-color: rgba(255,255,255,0.1);
}
.btn-one:hover::after {
    opacity: 0;
    transform: scale(0.1, 1);
}
p{
  margin: 10px;
  font-weight: bold;
  font-size: 24px;
}
li{
  margin: 10px;
  font-weight: bold;
  font-size: 24px;
  list-style:none;
}
li:nth-child(1){
  font-size: 30px;
  color:goldenrod;
  text-decoration: underline;
}
li:nth-child(2){
  font-size: 28px;
}
li:nth-child(3){
  font-size: 28px;
}
h1{
  font-size: 60px;
}
input{
  margin: 0;
  padding: 0;
  width: 300px;
  height: 40px;
  line-height: 1rem;
  font-size: 25px;
  text-align: center;
  font-weight: bold;
}
</style>