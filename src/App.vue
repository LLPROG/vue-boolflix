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
      this.axiosSet('movie')
      this.axiosSet('tv')
      this.arrCardsMovie = ''
      this.arrCardsTv = ''
    },
    axiosSet (typeSearch) {
      axios.get(this.api + '/search/' + typeSearch, {
        params: {
          api_key: 'dccfcea6793752dd574eef990cb9eace',
          language: 'it-IT',
          query: this.userInput.toLowerCase()
        }
      })
        .then((response) => {
          if (typeSearch === 'movie') {
            this.arrCardsMovie = response.data.results
            console.log(this.arrCardsMovie)
          } else {
            this.arrCardsTv = response.data.results
            console.log(this.arrCardsTv)
          }
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
  text-align: center;
}
</style>
