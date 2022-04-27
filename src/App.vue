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
  <input v-model="summoner">
  <button @click="getSummoner">Get {{ summoner }}</button>
  <pre>{{ results }}</pre>
</template>

<script>
const axios = require('axios').default
export default {
  name: 'App',

  data() {
    return {
      region: null,
      summoner: null,
      results: null
    }
  },
  methods: {
    async getSummoner() {
      axios.get(`http://localhost:3000/${this.region}/summoner/${this.summoner}`)
      .then((response) => {
        this.results = response.data;
      })
      .catch((error) => {
        this.results = error;
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
