<template>
    <div class="search">
        <h2>Type In your Search Term</h2>
    <form v-on:submit.prevent="getResult(query)">
        <input type="text" v-model="query"/>
        <h1>{{query}}</h1>
    </form>
    </div>
</template>

<script>
    export default {
        name: "search",
        data(){
            return{
                msg: "Search",
                query: "Erik"
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
               const myJson = await response.Js
              alert(JSON.stringify());
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>