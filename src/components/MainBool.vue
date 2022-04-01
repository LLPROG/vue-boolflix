<template>
  <div>
    <div class="deck"  v-for="movie in passedArreyMovie" :key="movie.backdrop_path">
      <div class="card">
        <div class="back">
          <h1 class="title">Titolo: {{ movie.title }}</h1>
          <h2>Titolo Originale: {{ movie.original_title }}</h2>
          <img class="flag" v-if="movie.original_language !== 'en' " :src="link + movie.original_language">
          <img class="flag" v-else :src="link + en">
          <div class="stars">
            Voto:
            <font-awesome-icon v-for="i in Math.round(movie.vote_average / 2)" :key="i" icon="fa-solid fa-star" />
            <font-awesome-icon v-for="i in 5 - Math.round(movie.vote_average / 2)" :key="i + 'vuoto'" icon="fa-regular fa-star" />
          </div>

          <h4 v-for="el in getCast(movie.id, 'movie')" :key="el._id">ciao</h4>

          <div v-if="movie.overview !== ''" class="overview">Trama: {{movie.overview}}</div>
        </div>
        <div class="front">
          <div v-if="movie.poster_path == null" class="no-poster">copertina non disponibile</div>
          <img v-else :src="poster + posterSize + movie.poster_path" :alt="movie.title">
        </div>
      </div>
    </div>

    <div class="deck"  v-for="serie in passedArreyTv" :key="serie.backdrop_path">
      <div class="card">
        <div class="back">
          <h1 class="title">{{ serie.name }}</h1>
          <h2>{{ serie.name }}</h2>
          <img class="flag" v-if="serie.original_language !== 'en' " :src="link + serie.original_language">
          <img class="flag" v-else :src="link + en">
          <div class="stars">
            Voto:
            <font-awesome-icon v-for="i in Math.round(serie.vote_average / 2)" :key="i" icon="fa-solid fa-star" />
            <font-awesome-icon v-for="i in 5 - Math.round(serie.vote_average / 2)" :key="i + 'vuoto'" icon="fa-regular fa-star" />
          </div>
          <div v-if="serie.overview !== ''" class="overview">Trama: {{serie.overview}}</div>
        </div>
        <div class="front">
          <div v-if="serie.poster_path == null" class="no-poster">copertina non disponibile</div>
          <img v-else :src="poster + posterSize + serie.poster_path" :alt="serie.title">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
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
      posterSize: 'w342/',
      api: 'https://api.themoviedb.org/3'
    }
  },
  methods: {
    getCast (id, type) {
      axios.get(this.api + '/' + type + '/' + id + '/credits', {
        params: {
          api_key: 'dccfcea6793752dd574eef990cb9eace',
          language: 'it-IT'
        }
      })
        .then((response) => {
          console.log(response.data.cast.slice(0, 5))
          return response.data.cast.slice(0, 5)
        })
    }
  }
}
</script>

<style lang="scss" scoped>
.deck {
  background-color: transparent;
  width: 342px;
  height: 515px;
  perspective: 1000px;

  &:hover .card {
  transform: rotateY(180deg);
  }
  .card {
    width: 100%;
    height: 100%;
    transform-style: preserve-3d;
    -webkit-transition: all .5s linear;
    transition: all .5s linear;
    -webkit-box-shadow: 0px 0px 13px 1px rgba(0,0,0,0.59);
    box-shadow: 0px 0px 13px 1px rgba(0,0,0,0.59);
    .flag {
      margin: 1rem 0;
      width: 10%;
    }
    .title {
      margin: 1rem 0;
    }
    .back {
      padding: 0.5rem;
      position: absolute;
      width: 100%;
      height: 100%;
      background-color: black;
      color: white;
      transform: rotateY(180deg);
      backface-visibility: hidden;
      overflow-y:auto;
    }
    .front {
      width: 100%;
      height: 100%;
      text-align: center;
      overflow:hidden;
      z-index:-1;
      display: block;
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }
  }
}

</style>
