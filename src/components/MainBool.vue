<template>
  <div>
    <div>film</div>
    <div class="cont-movies">
      <card-bool v-for="movie in passedArreyMovie" :key="movie.id" :card-data="movie"/>
    </div>
    <div>serie tv</div>
    <div class="cont-series">
      <card-bool v-for="serie in passedArreyTv" :key="serie.id" :card-data="serie"/>
    </div>
  </div>
</template>

<script>
import CardBool from './CardBool.vue'

export default {
  name: 'MainBool',
  props: {
    passedValue: String,
    passedArreyMovie: [],
    passedArreyTv: []
  },
  components: {
    CardBool
  }
}
</script>

<style lang="scss" scoped>
.cont-movies,
.cont-series {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 1rem;
  text-align: left;
}
</style>
