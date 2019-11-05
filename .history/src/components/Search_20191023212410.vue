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
                query: ""
            }
        },
        methods: {
           async getResult(){
             await fetch('https://images-api.nasa.gov/search?q=' + this.query + '&media_type=image',{
                  credentials: "same-origin",
               mode: 'cors',
                header: {
            'Access-Control-Allow-Origin':'*',
                }
               }
               .then(response => response.json())
               .then(data => {
                 alert(JSON.stringify(response));
               })
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>