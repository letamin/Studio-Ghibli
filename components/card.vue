<template>
    <div class="movie-card card">
      <nuxt-link :to="`/movie/${id}`">
        <div class="card-body">
          <h5 class="card-title">{{ title }} - {{ originalTitle }}</h5>
          <p class="card-text">{{ description }}</p>
          <p class="card-text">Director: {{ director }}</p>
          <p class="card-text">Release Date: {{  releaseDate }}</p>
        </div>
      </nuxt-link>
   </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    },
    originalTitle: {
      type: String
    },
    description: {
      type: String
    },
    director: {
      type: String
    },
    releaseDate: {
      type: String
    },
    id: {
      type: String
    }
  }
}
</script>

<style>

</style>
