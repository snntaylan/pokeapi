<template>
  <div id="app">
    <h1 id="title">Pokemon Finder-API</h1>
    <PokeApi/>
  </div>
</template>

<script>
import PokeApi from "./components/PokeApi.vue";

export default {
  name: "app",
  components: {
    PokeApi
  }
};
</script>

<style>
h1 {
  color: white;
}
#title {
  color: cornflowerblue;
}

body {
  margin: 20px;
  padding: 20p;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
  background-image: url(../public/pokeapi-bg.jpg);
}

#app {
  font-family: "Source Sans Pro, Arial, sans-serif";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #325e8a;
  margin-top: 100px;
}
</style>
