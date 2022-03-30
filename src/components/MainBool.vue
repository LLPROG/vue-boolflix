<template>
  <div>
    <div class="card" v-for="movie in passedArreyMovie" :key="movie.id">
      <h1>{{ movie.title }}</h1>
      <h2>{{ movie.original_title }}</h2>
      <img class="flag" v-if="movie.original_language !== 'en' " :src="link + movie.original_language">
      <img class="flag" v-else :src="link + en">
      <div class="stars">
        <!-- <h4>{{ Math.round(movie.vote_average / 2) }}</h4> -->
        <font-awesome-icon v-if="Math.round(movie.vote_average / 2) < 1" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(movie.vote_average / 2) < 2" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(movie.vote_average / 2) < 3" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(movie.vote_average / 2) < 4" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(movie.vote_average / 2) < 5" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />
      </div>
      <img :src="poster + posterSize + movie.poster_path" :alt="movie.title">
    </div>

    <div class="card" v-for="serie in passedArreyTv" :key="serie.id">
      <h1>{{ serie.name }}</h1>
      <h2>{{ serie.name }}</h2>
      <img class="flag" v-if="serie.original_language !== 'en' " :src="link + serie.original_language">
      <img class="flag" v-else :src="link + en">
      <div class="stars">
        <!-- <h4>{{ Math.round(serie.vote_average / 2) }}</h4> -->
        <font-awesome-icon v-if="Math.round(serie.vote_average / 2) < 1" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(serie.vote_average / 2) < 2" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(serie.vote_average / 2) < 3" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(serie.vote_average / 2) < 4" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />

        <font-awesome-icon v-if="Math.round(serie.vote_average / 2) < 5" icon="fa-regular fa-star" />
        <font-awesome-icon v-else icon="fa-solid fa-star" />
      </div>
      <img :src="poster + posterSize + serie.poster_path" :alt="serie.title">

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
      poster: 'https://image.tmdb.org/t/p/',
      posterSize: 'w342/'
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
