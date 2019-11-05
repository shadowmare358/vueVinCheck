<template>
    <div class="search">
        <h2>Best selling cars</h2>
    <form v-on:submit.prevent="getResult(query)">
        <input type="text" v-model="query"/>
        <h1>{{query}}</h1>
    </form>
       <img v-bind:src="results"/>
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
            const api_key = "NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu"
           async getResult(){
              const response = await fetch(`http://api.marketcheck.com/v1/popular/cars?api_key=${api_key}&car_type=new`,{
                  credentials: "same-origin",
               mode: 'cors',
                header: {
            'Access-Control-Allow-Origin':'*',
                }
               })
               const myJson = await response.json();
              this.results = myJson.collection.items[0].links[0].href;
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>