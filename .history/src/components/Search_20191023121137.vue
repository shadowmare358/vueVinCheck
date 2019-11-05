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
            getResult(){

               axios.get('http://www.reddit.com/r/pics.js',{
                   headers: {'Access-Control-Allow-Origin': '*'}
               })
               .then(response => {alert(response)});
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>