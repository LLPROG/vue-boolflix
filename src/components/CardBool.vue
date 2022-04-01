<template>
  <div>
    <div class="deck">
      <div class="card">
        <div class="back">
          <h1 class="title">Titolo: {{ CardData.title }}</h1>
          <h2>Titolo Originale: {{ CardData.original_title }}</h2>
          <img class="flag" v-if="CardData.original_language !== 'en' " :src="link + CardData.original_language">
          <img class="flag" v-else :src="link + en">
          <div class="stars">
            Voto:
            <font-awesome-icon v-for="i in Math.round(CardData.vote_average / 2)" :key="i" icon="fa-solid fa-star" />
            <font-awesome-icon v-for="i in 5 - Math.round(CardData.vote_average / 2)" :key="i + 'vuoto'" icon="fa-regular fa-star" />
          </div>
          <div class="cast">
            Attori:
            <h4 v-for="el in arrCast" :key="el._id">{{  el.name }}</h4>
          </div>

          <div v-if="CardData.overview !== ''" class="overview">Trama: {{CardData.overview}}</div>
        </div>
        <div class="front">
          <div v-if="CardData.poster_path == null" class="no-poster">copertina non disponibile</div>
          <img v-else :src="poster + posterSize + CardData.poster_path" :alt="CardData.title">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'CardBool',
  props: {
    CardData: Object
  },
  data () {
    return {
      link: 'https://countryflagsapi.com/png/',
      en: 'gb',
      poster: 'https://image.tmdb.org/t/p/',
      posterSize: 'w342/',
      api: 'https://api.themoviedb.org/3',
      arrCast: [],
      type: 'movie'
    }
  },
  created () {
    this.castForMovie()
    this.castForSeries()
  },
  methods: {
    castForMovie () {
      axios.get(this.api + '/movie/' + this.CardData.id + '/credits', {
        params: {
          api_key: 'dccfcea6793752dd574eef990cb9eace',
          language: 'it-IT'
        }
      })
        .then((response) => {
          console.log(response.data.cast.slice(0, 5))
          this.arrCast = response.data.cast.slice(0, 5)
        })
        .catch(function (error) {
          console.log(error.toJSON())
        })
    },
    castForSeries () {
      axios.get(this.api + '/tv/' + this.CardData.id + '/credits', {
        params: {
          api_key: 'dccfcea6793752dd574eef990cb9eace',
          language: 'it-IT'
        }
      })
        .then((response) => {
          console.log(response.data.cast.slice(0, 5))
          this.arrCast = response.data.cast.slice(0, 5)
        })
        .catch(function (error) {
          console.log(error.toJSON())
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

      .cast {
        margin: 0.5rem 0;
      }
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
