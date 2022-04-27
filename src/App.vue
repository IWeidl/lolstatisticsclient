<template>
  <select v-model="region">
    <option>OC1</option>
    <option>NA1</option>
    <option>EUN1</option>
    <option>EUW1</option>
    <option>JP1</option>
    <option>KR</option>
    <option>BR1</option>
    <option>TR1</option>
    <option>RU</option>
  </select>
  <input v-model="summonerSearch">
  <button @click="getSummoner">Get {{ summonerSearch }}</button>
  <BasicSummonerInfo v-if="results" :name="results[0]" :level="results[1]" />
</template>

<script>
const axios = require('axios').default
import BasicSummonerInfo from "@/components/BasicSummonerInfo";
export default {
  name: 'App',
  components: {
    BasicSummonerInfo
  },

  data() {
    return {
      region: null,
      summonerSearch: null,
      results: null,
    }
  },
  methods: {
    async getSummoner() {
      axios.get(`http://localhost:3000/${this.region}/summoner/${this.summonerSearch}`)
      .then((response) => {
        this.results = [response.data.name, response.data.summonerLevel]
      })
      .catch((error) => {
        console.log(error)
      })
      .then(() => {
      })

    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
