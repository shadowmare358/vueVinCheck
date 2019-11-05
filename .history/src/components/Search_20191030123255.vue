<template>
  <div class="search">
    <h2>CAR INFO PAGE</h2>
    <button v-on:click="getResults()">Show Ten Best Sellers In US</button>
    <button v-on:click="getVIN()">Decode VIN</button>
    <input v-model="vin" v-on:keyup.enter="getVIN()">
    <div v-if="!carResults"></div>
    <ul>
        <li v-for="result in carResults" v-bind:key="result.id">{{result.make}} {{result.model}} Number of cars sold: {{result.count}}</li>
        <img v-for="item in imagesResults" v-bind:key="item.id" :src="item.image.thumbnailLink"/>
        <li v-for="result in vinResults" v-bind:key="result.id">{{result.year}}</li>
    </ul>
    <p>{{carResults.model}}</p>
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
      vinResults: "",
      testQuery: "flower",
      modelInfo: "",
      vin: ""
    };
  },
  methods: {
    async getResults() {
        const marketApiKey = "NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu"
      await fetch(
        `https://marketcheck-prod.apigee.net/v1/popular/cars?api_key=${marketApiKey}&car_type=new`
      )
        .then(response => response.json())
        .then(myJson => this.carResults = myJson.slice(0,10))
        .catch(err => alert(`Cannot get requested data ${err}`));
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
   // const marketApiKey = "NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu"
     await fetch(
        `http://api.marketcheck.com/v1/vin/1FAHP3F28CL148530/specs?api_key=NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu`,{
           mode: "cors",
          headers: {
            host: "marketcheck-prod.apigee.net",
            "Content-Type": "application/json",
            "Access-Control-Allow-Credentials": true
          }
        }
      )
        .then(response => response.json())
        .then(myJson => this.vinResults = myJson)
        .catch(err => alert(`Cannot get requested data ${err}`));
  }
}
};
</script>
<style  scoped>
button{
  margin: 10px;
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
h2{
  font-size: 40px;
}
</style>