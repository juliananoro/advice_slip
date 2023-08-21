<template>
  <Header />
  <div id="container">
    <span class="card" id="card1">
      <Random />
    </span>
    <span class="card" id="card2">
      <ById />
    </span>
    <span id="card3">
      <ByQuery />
    </span>
  </div>
</template>

<script>
  import Header from './components/Header.vue'
  import Random from './components/Random.vue'
  import ById from './components/ById.vue'
  import ByQuery from './components/ByQuery.vue'

  export default {
    name: 'App',
    components: {
      Header,
      Random,
      ById,
      ByQuery
    },
    data() {
      return{
      }
    }
  }
</script>

<style>
  body {
    background-color: #4b2f64;
    color: white;
    font-family: 'Macondo', sans-serif;
  }
  
  #container {
    background-color: white;
    display: grid;
    grid-template-areas:
      "card1 card2"
      "card3 card3";
    grid-template-columns: 1fr 1fr;
    margin: 2%;
    padding: 2%;
    border-radius: 12px;
  }

  .card {
    background-color: #a384be;
    padding: 4%;
    margin: 2%;
    border-radius: 12px;
  }

  p {
    font-family: 'Macondo', 'Poppins', sans-serif;
    font-size: 20px;
    margin: 0px;
  }

  h2 {
    margin: 0px;
  }

  #card3 {
    background-color: #a384be;
    padding: 2%;
    margin: 1%;
    border-radius: 12px;
    grid-column: span 2;
  }
</style>