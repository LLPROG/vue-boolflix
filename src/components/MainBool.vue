<template>
  <div>
    <div class="card" v-for="movie in passedArrey" :key="movie.id">
      <h1>{{ movie.title }}</h1>
      <h2>{{ movie.original_title }}</h2>
      <h3>{{ movie.original_language }}</h3>
      <h4>{{ movie.vote_average }}</h4>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainBool',
  props: {
    passedValue: String,
    passedArrey: []
  }
}
</script>

<style lang="scss" scoped>

</style>
