<template>
    <div class="search">
    <form c-on:submit.prevent="getResult(query)">
        <input type="text" v-model="query"/>
        <h1></h1>
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
            getResult(query){
                alert(query);
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>