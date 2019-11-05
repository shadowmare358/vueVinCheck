<template>
    <div class="search">
        <h2>Type In your Search Term</h2>
    <form v-on:submit.prevent="getResult(query)">
        <input type="text" v-model="query"/>
        <h1>{{query}}</h1>
    </form>
        <div v-if="results">
   <div v-for="result in results" v-bind:key="result">
       <img v-bind:src="result"/>
    </div>
    </div>
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
              const response = await fetch('https://images-api.nasa.gov/search?q=' + this.query + '&media_type=image',{
                  credentials: "same-origin",
               mode: 'cors',
                header: {
            'Access-Control-Allow-Origin':'*',
                }
               })
               const myJson = await response.json();
              alert(JSON.stringify(myJson.collection.items[0].links[0].href));
              this.results = JSON.stringify(myJson.collection.items[0].href);
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>