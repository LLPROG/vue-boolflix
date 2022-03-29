<template>
  <div>
    <card-bool :passed-value="passedValue"/>
  </div>
</template>

<script>
import CardBool from './CardBool.vue'

export default {
  name: 'MainBool',
  components: {
    CardBool
  },
  props: {
    passedValue: String
  },
  data () {
    return {
      api: 'https://api.themoviedb.org/3/movie/550?',
      api_key: 'api_key=dccfcea6793752dd574eef990cb9eace'
    }
  }

}
</script>

<style lang="scss" scoped>

</style>
