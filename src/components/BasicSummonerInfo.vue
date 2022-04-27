<template>
  <h1>Summoner: {{ name }}</h1>
  <h2>Level: {{ level }}</h2>
</template>

<script>
export default {
  name: "BasicSummonerInfo",
  props: {
    name: String,
    level: Number
  }
}
</script>

<style scoped>

</style>
