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

               mode: 'no-cors'
               })
               const myJson = await response.json();
              this.results =myJson;
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>