<template>
  <div class="search">
    <h2>Best</h2>
    <button v-on:click="getResults()">Show Best Sellers</button>
    <div v-if="!results"></div>
    <ul>
        
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
      await fetch(
        "https://marketcheck-prod.apigee.net/v1/popular/cars?api_key=NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu&car_type=new",
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
        .then(myJson => (this.results = myJson[0]))
        .catch(err => alert(`Cannot get requested data ${err}`));
    }
  }
};
</script>
<style lang="scss" scoped>
</style>