<template>
    <div class="search">
    <form c-on:submit.prevent="getResult(query)">
        <input type="text" v-model="query"/>
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
        }
    }
</script>

<style lang="scss" scoped>

</style>