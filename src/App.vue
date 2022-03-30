<template>
  <div id="app">
    <header-bool @onclick="saveValue"/>
    <main-bool class="main" :passed-value="userInput" :passed-arrey="arrCards"/>
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
      api: 'https://api.themoviedb.org/3/search/movie?api_key=dccfcea6793752dd574eef990cb9eace&query=',
      arrCards: null
    }
  },
  methods: {
    saveValue (passedValue) {
      this.userInput = passedValue
      console.log(passedValue)
      axios.get(this.api + this.userInput.split(' ').join('+'))
        .then((response) => {
          this.arrCards = response.data.results
        })
    }
  }
}
</script>

<style lang="scss">
@import './assets/style.scss';
.main {
  width: 100%;
  min-height: calc(100vh - 83px);
  background-color: gray;
}
</style>
