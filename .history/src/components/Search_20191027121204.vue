<template>
  <div class="search">
    <h2>Car info</h2>
    <button v-on:click="getResults()">Show Best Sellers</button>
    <button v-on:click="getImageResults()">Show Images</button>
    <div v-if="!carResults"></div>
    <ul>
        <li v-for="result in carResults" v-bind:key="result.id">{{result.make}} {{result.model}} Number of cars sold: {{result.count}}</li>
    </ul>
    <ul>
        <li v-for="img in imagesResults" v-bind:key="img.id">{{img.items}}</li>
    </ul>
    <p>{{carResults.model}}</p>
    <input type="text" v-model="query" />
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
      imagesResults: "",
      testQuery: "flower"
    };
  },
  methods: {
    async getResults() {
        const marketApiKey = "NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu"
      await fetch(
        `https://marketcheck-prod.apigee.net/v1/popular/cars?api_key=${marketApiKey}&car_type=new`,
        {
          mode: "cors",
          headers: {
            host: "marketcheck-prod.apigee.net",
            "Access-Control-Allow-Origin": "*",
            "Content-Type": "multipart/form-data",
            "Access-Control-Allow-Credentials": true
          }
        }
      )
        .then(response => response.json())
        .then(myJson => this.carResults = myJson)
        .catch(err => alert(`Cannot get requested data ${err}`));
    },
    async getImageResults(){
        // const cxKey = '001912728085642910227:akqkacx3uim';
        // const googleApiKey = 'AIzaSyCAJ2rKXL-X_daAy2dveCO--E5ciLgIK6k';
       await fetch(
        `https://www.googleapis.com/customsearch/v1?q=honda_jazz&key=AIzaSyCAJ2rKXL-X_daAy2dveCO--E5ciLgIK6k&cx=001912728085642910227:akqkacx3uim&searchType=image&fileType=jpg&imgSize=small&alt=json`,{
              headers: {
            "Access-Control-Allow-Origin": "*",
            "mode": "cors",
            "Content-Type": "multipart/form-data",
            "Access-Control-Allow-Credentials": true
          }
        }
      )
        .then(response => response.json())
        .then(myJson => this.imagesResults=myJson)
        .catch(err => alert(`Cannot get requested data ${err}`));
    }
  }
};
</script>
<style  scoped>
li{
    list-style: none;
}
</style>