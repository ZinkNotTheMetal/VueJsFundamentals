<template>
  <div>
    <h2>Hero</h2>
    
    <ul>
      <li 
        v-for="hero in heros" 
        :key="hero.id"
        @click="selectHero(hero)"
        :class="{highlight: selectedHero === hero }">
        {{ hero.name }}
      </li>
    </ul>

    <div v-if="selectedHero">
      {{ selectedHero.name }} has been selected!
    </div>
  </div>
</template>

<script>
export default {

  name: "Heroes",
  data() {
    return {
      selectedHero: undefined,
      heros: [
        { id: 1, name: "John" },
        { id: 2, name: "Dan"},
        { id: 3, name: "Scott"}
      ]
    };
  },
  methods: {
    selectHero(hero) {
      this.selectedHero = hero;
    }
  }
};
</script>

<style lang="css">
li {
  list-style: none;
  width: 200px;
  cursor: pointer;
}

.highlight {
  background-color: yellow;
}
</style>
