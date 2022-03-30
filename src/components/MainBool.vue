<template>
  <div>
    <div class="deck"  v-for="movie in passedArreyMovie" :key="movie.id">
      <div class="card">
        <div class="back">
          <h1 class="title">Titolo: {{ movie.title }}</h1>
          <h2>Titolo Originale: {{ movie.original_title }}</h2>
          <img class="flag" v-if="movie.original_language !== 'en' " :src="link + movie.original_language">
          <img class="flag" v-else :src="link + en">
          <div class="stars">
            Voto:
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
          <div v-if="movie.overview !== ''" class="overview">Trama: {{movie.overview}}</div>
        </div>
        <div class="front">
          <div v-if="movie.poster_path == null" class="no-poster">copertina non disponibile</div>
          <img v-else :src="poster + posterSize + movie.poster_path" :alt="movie.title">
        </div>
      </div>
    </div>

    <div class="deck"  v-for="serie in passedArreyTv" :key="serie.id">
      <div class="card">
        <div class="back">
          <h1 class="title">{{ serie.name }}</h1>
          <h2>{{ serie.name }}</h2>
          <img class="flag" v-if="serie.original_language !== 'en' " :src="link + serie.original_language">
          <img class="flag" v-else :src="link + en">
          <div class="stars">
            Voto:
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
      overflow:hidden;
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
