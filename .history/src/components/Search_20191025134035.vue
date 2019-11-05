<template>
  <div class="search">
    <h2>Car info</h2>
    <button v-on:click="getImageResults()">Show Best Sellers</button>
    <div v-if="!results"></div>
    <ul>
        <li v-for="result in results" v-bind:key="result.id">{{result.make}} {{result.model}} Number of cars sold: {{result.count}}</li>
    </ul>
    <p>{{results.model}}</p>
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
      results: ""
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
        .then(myJson => alert(myJson))
        .catch(err => alert(`Cannot get requested data ${err}`));
    },
    async getImageResults(query){
       await fetch(
        `" `https://www.googleapis.com/customsearch/v1?q=honda_jazz&key=AIzaSyCAJ2rKXL-X_daAy2dveCO--E5ciLgIK6k&cx=001912728085642910227:akqkacx3uim&searchType=image&fileType=jpg&imgSize=small&alt=json"
      )
        .then(response => response.json())
        .then(myJson => alert(myJson))
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