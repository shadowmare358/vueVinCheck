<template>
    <div class="search">
        <h2>Best</h2>
    <form v-on:submit.prevent="getResults(query)">
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
              const response = await fetch('http://api.marketcheck.com/v1/popular/cars?api_key=NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu&car_type=used&state=TX',{
               mode: 'no-cors',
               headers: {
                   'host': 'marketcheck-prod.apigee.net'
               }
               })
               const myJson = await response.json();
               alert(JSON.stringify(myJson));
            //    const myJson = await response.json();
            //   this.results =myJson;
            },
            async getResults(){
             const resp = await fetch("https://marketcheck-prod.apigee.net/v1/search?api_key=NuJ2q06UO5TRrFU2QfhteMzvIPRz5sNu&car_type=used&vins=1FTEW1EG8HFA58169&match=year,make,model&plot=true&stats=price,miles&latitude=34.02&longitude=-118.28&radius=100", {
               mode: 'no-cors',
               headers: {
                   'host': 'marketcheck-prod.apigee.net'
               }
               })
              .catch((error) => {
                  alert("Wystąpił błąd " + error);
              })


            }
        }
    }
</script>

<style lang="scss" scoped>

</style>