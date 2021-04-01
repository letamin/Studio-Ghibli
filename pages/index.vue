<template>
  <div class="main-container container">
    <Card
      v-for="movie in movies"
      :key="movie.id"
      :title="movie.title"
      :originalTitle="movie.original_title"
      :description="movie.description"
      :director="movie.director"
      :releaseDate="movie.release_date"
      :id="movie.id"
    />
    <infinite-loading spinner="spiral" @infinite="infiniteScroll"></infinite-loading>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData ({ $axios }) {
    const movies = await $axios.$get('https://ghibliapi.herokuapp.com/films')
    return { movies }
  },
  methods: {
    // Test infinite scroll
    infiniteScroll ($state) {
      setTimeout(() => {
        axios.get('https://ghibliapi.herokuapp.com/films').then((response) => {
          if (response.length > 1) {
            response.data.forEach((item) => {
              this.movies.push(item)
            })
            $state.loaded()
          } else {
            $state.complete()
          }
        }).catch((err) => {
          console.log(err)
        })
      }, 500)
    }
  }
}
</script>

<style></style>
