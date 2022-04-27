<template>
  <button @click="getSummoner">GET EXLEX</button>
  <pre>{{ results }}</pre>
</template>

<script>
const axios = require('axios').default
export default {
  name: 'App',

  data() {
    return {
      results: null
    }
  },
  methods: {
    async getSummoner() {
      axios.get('http://localhost:3000/oc1/summoner/exlex')
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
