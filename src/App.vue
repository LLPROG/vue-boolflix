<template>
  <div id="app">
    <header-bool @onclick="saveValue"/>
    <main-bool class="main" :passed-value="userInput" />
  </div>
</template>

<script>
import HeaderBool from './components/HeaderBool.vue'
import MainBool from './components/MainBool.vue'

export default {
  name: 'App',
  components: {
    HeaderBool,
    MainBool
  },
  data () {
    return {
      userInput: ''
    }
  },
  methods: {
    saveValue (passedValue) {
      this.userInput = passedValue
      console.log(this.userInput)
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
