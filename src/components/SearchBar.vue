<template>
  <div>
    <label for="input">
      <input type="text" v-model="userInput" placeholder="cerca film o serie tv ">
      <button @click="$emit('onclick', userInput)">
        cerca
      </button>
    </label>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    searchInApi () {
      console.log('ciao')
    }
  },
  data () {
    return {
      userInput: ''
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
