<template>
  <Loading v-if="$fetchState.pending" />
  <div v-else class="container single-movie">
    <h1>{{ this.movie.title }}</h1>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'single-movie',
  data() {
    return {
      movie: null,
    }
  },
  async fetch() {
    await this.getSingleMovie()
  },
  fetchDelay: 1000,
  methods: {
    async getSingleMovie() {
      const data = axios.get(
        `https://api.themoviedb.org/3/movie/${this.$route.params.movieId}?api_key=b5113b33ec1552d764dd0ded651147b3&language=en-US`
      )
      const result = await data
      this.movie = result.data
    },
  },
}
</script>

<style lang="scss" scoped>
</style>
