<template>
    <div class="search">
        <h2>Best selling cars</h2>
        <button v-on:click="getResult(query)"/>
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
               //const api_key = "NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu";
              const response = await fetch(`https://images-api.nasa.gov/search?q=mars&media_type=image`,{
                  credentials: "same-origin",
               mode: 'no-cors',
                header: {
            'Access-Control-Allow-Origin':'*',
                }
               })
               const myJson = await response.json();
              alert(myJson);
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>