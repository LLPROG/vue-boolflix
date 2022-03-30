<template>
  <div>
    <div class="card" v-for="movie in passedArreyMovie" :key="movie.id">
      <h1>{{ movie.title }}</h1>
      <h2>{{ movie.original_title }}</h2>
      <img class="flag" v-if="movie.original_language !== 'en' " :src="link + movie.original_language">
      <img class="flag" v-else :src="link + en">
      <h4>{{ movie.vote_average }}</h4>
    </div>

    <div class="card" v-for="movie in passedArreyTv" :key="movie.id">
      <h1>{{ movie.name }}</h1>
      <h2>{{ movie.name }}</h2>
      <img class="flag" v-if="movie.original_language !== 'en' " :src="link + movie.original_language">
      <img class="flag" v-else :src="link + en">
      <h4>{{ movie.vote_average }}</h4>
    </div>
  </div>
</template>

<script>

export default {
  name: 'MainBool',
  props: {
    passedValue: String,
    passedArreyMovie: [],
    passedArreyTv: []
  },
  data () {
    return {
      link: 'https://countryflagsapi.com/png/',
      en: 'gb'
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
