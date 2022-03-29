<template>
  <header>
    <h1>
      Boolflix
    </h1>
    <search-bar class="search-bar" @onclick="onclick"/>
  </header>
</template>

<script>
import SearchBar from './SearchBar.vue'
export default {
  name: 'HeaderBool',
  components: {
    SearchBar
  },
  methods: {
    onclick (userInput) {
      this.$emit('onclick', userInput)
    }
  }
}
</script>

<style lang="scss" scoped>
header {
  width: 100%;
  padding: 1rem;
  display: flex;
  background-color: black;
  color: red;

  .search-bar {
    margin-left: auto;
    display: inline-block;
    padding: 1rem;
  }
}
</style>
