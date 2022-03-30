<template>
  <div id="app">
    <header-bool @onclick="saveValue"/>
    <main-bool class="main"
      :passed-value="userInput"
      :passed-arrey-movie="arrCardsMovie"
      :passed-arrey-tv="arrCardsTv"
    />
  </div>
</template>

<script>
import HeaderBool from './components/HeaderBool.vue'
import MainBool from './components/MainBool.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderBool,
    MainBool
  },
  data () {
    return {
      userInput: '',
      api: 'https://api.themoviedb.org/3',
      arrCardsMovie: null,
      arrCardsTv: null
    }
  },
  methods: {
    saveValue (passedValue) {
      this.userInput = passedValue
      console.log(passedValue)
      // movie
      axios.get(this.api + '/search/movie', {
        params: {
          api_key: 'dccfcea6793752dd574eef990cb9eace',
          language: 'it-IT',
          query: this.userInput.toLowerCase()
        }
      })
        .then((response) => {
          this.arrCardsMovie = response.data.results
          console.log(this.arrCardsMovie)
        })
      // serie tv
      axios.get(this.api + '/search/tv', {
        params: {
          api_key: 'dccfcea6793752dd574eef990cb9eace',
          language: 'it-IT',
          query: this.userInput.toLowerCase()
        }
      })
        .then((response) => {
          this.arrCardsTv = response.data.results
          console.log(this.arrCardsTv)
        })
    }
  }
}
</script>

<style lang="scss">
@import './assets/style.scss';
.main {
  background-color: gray;
  width: 100%;
  min-height: calc(100vh - 83px);
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
</style>
