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

           async getResult(){
               const api_key = "NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu";
              const response = await fetch(`http://api.marketcheck.com/v1/popular/cars?api_key=${api_key}&car_type=new`
               const myJson = await response.json();
              alert(myJson);
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>