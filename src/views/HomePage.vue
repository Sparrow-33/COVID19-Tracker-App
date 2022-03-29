<template>
  <main v-if="!loading">
Show Data
  </main>

  <main v-else class="flex flex-col align-center justify-center text-center" >
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <img :src="loadingImage" class="w-24 m-auto">
  </main>
</template>

<script>
export default {
  name: 'HomePage',
  data(){
   return {
     loading : true,
     title: 'Global',
     dataDate: '',
     status:{},
     countries:[],
     loadingImage: require('../assets/D1.gif')
   }
  },
  props: {
  },
  methods:{
  async fetchCovidData(){
  const responce = await fetch('https://api.covid19api.com/summary')
  const data = await responce.json()
    return data
  },
  },
async created() {
    const data = await this.fetchCovidData()
    this.dataDate = data.Date
    this.status = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
