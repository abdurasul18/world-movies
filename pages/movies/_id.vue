<template>
  <div>
    <div
      v-if="!$fetchState.pending"
      class="movie-single relative bg-no-repeat bg-cover bg-center px-4"
      :style="`background-image:url(https://image.tmdb.org/t/p/w500/${movie.poster_path}); min-height:100vh`"
    >
      <div class="container text-white pt-32 relative z-10">
        <h1 class="text-3xl">{{ movie.title }}</h1>
        <p class="text-xl">{{ movie.overview }}</p>
      </div>
    </div>
    <div class="absolute inset-0 flex items-center justify-center" v-else>
      <img src="@/assets/images/loader.svg" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: this.movie.title,
    }
  },
  data() {
    return {
      movie: {},
    }
  },
  methods: {
    async getMovie() {
      const result = await this.$axios.get(
        `movie/${this.$route.params.id}?api_key=fa61e6fa7724edd99048bc5f0b11ae72`
      )
      this.movie = result.data
    },
  },
  async fetch() {
    await this.getMovie()
  },
   fetchDelay : 2000,
}
</script>

<style scoped>
.movie-single::after {
  content: '';
  position: absolute;
  inset: 0;
  opacity: 0.3;
  z-index: 1;
  @apply bg-secondary;
}
</style>