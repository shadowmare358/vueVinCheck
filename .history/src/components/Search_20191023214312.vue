<template>
    <div class="search">
        <h2>Type In your Search Term</h2>
    <form v-on:submit.prevent="getResult(query)">
        <input type="text" v-model="query"/>
        <h1>{{query}}</h1>
    </form>
    </div>
    <div v-if="results"
    <div v-for="result in results">

    </div>
</template>

<script>
    export default {
        name: "search",
        data(){
            return{
                msg: "Search",
                query: "Erik",
                results: ''
            }
        },
        methods: {
           async getResult(){
               const query = "Mars";
              const response = await fetch('https://images-api.nasa.gov/search?q=' + query + '&media_type=image',{
                  credentials: "same-origin",
               mode: 'cors',
                header: {
            'Access-Control-Allow-Origin':'*',
                }
               })
               const myJson = await response.json();
              alert(JSON.stringify(myJson.collection.items));
              this.results = JSON.stringify(myJson.collection.items);
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>