<template>
  <div>
    <div class="card" v-for="movie in passedArreyMovie" :key="movie.id">
      <h1>{{ movie.title }}</h1>
      <h2>{{ movie.original_title }}</h2>
      <img class="flag" v-if="movie.original_language !== 'en' " :src="link + movie.original_language">
      <img class="flag" v-else :src="link + en">
      <h4>{{ movie.vote_average }}</h4>
      <img :src="poster + movie.poster_path" :alt="movie.title">
    </div>

    <div class="card" v-for="serie in passedArreyTv" :key="serie.id">
      <h1>{{ serie.name }}</h1>
      <h2>{{ serie.name }}</h2>
      <img class="flag" v-if="serie.original_language !== 'en' " :src="link + serie.original_language">
      <img class="flag" v-else :src="link + en">
      <h4>{{ serie.vote_average }}</h4>
      <img :src="poster + serie.poster_path" :alt="serie.title">

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
      en: 'gb',
      poster: 'https://image.tmdb.org/t/p/w500/'
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
