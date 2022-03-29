<template>
  <div>
    <h1 class="title"> title</h1>
    <h2 class="original-title"></h2>
    <div class="lang"></div>
    <div class="vote"></div>
  </div>
</template>

<script>
export default {
  name: 'CardBool',
  props: {
    passedValue: String
  },
  methods: {
    console () {
      console.log(this.passedValue)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
