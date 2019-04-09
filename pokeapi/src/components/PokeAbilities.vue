<template>
  <div class="poke-abilities">
    <h2>Abilities of {{pokemon.name}}</h2>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-bind:key="i"
        v-for="(ability,i) in pokemon.abilities"
      >{{ability.ability.name}}</li>
      <h1 class="error" v-if="error" v-bind:error="error">{{error}}</h1>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Abilities",
  props: {
    pokemon: Object,
    default: null
  }
};
</script>

<style scoped>
.abilities {
  width: 100px;
}
.error {
  color: red;
}
</style>