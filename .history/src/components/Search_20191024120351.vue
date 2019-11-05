<template>
    <div class="search">
        <h2>Best</h2>
    <form v-on:submit.prevent="getResult(query)">
        <input type="text" v-model="query"/>
        <h1>{{query}}</h1>
    </form>
       <p>{{results}}</p>
    </div>


</template>

<script>
    export default {
        name: "search",
        data(){
            return{
                msg: "Search",
                query: "",
                results: ''
            }
        },
        methods: {
           async getResult(){
              const response = await fetch('http://api.marketcheck.com/v1/popular/cars?api_key=NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu&car_type=used&state=TX',{
               mode: 'no-cors',
               headers: {
                   'host': 'marketcheck-prod.apigee.net'
               }
               })
               alert(JSON.stringify(response.json());
            //    const myJson = await response.json();
            //   this.results =myJson;
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>