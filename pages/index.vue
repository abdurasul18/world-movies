<template>
  <div>
    <Header />
    <div class="container mx-auto px-4 md:px-0" v-if="!$fetchState.pending">
      <div class="py-4 flex items-center">
        <input
          v-model.lazy="searchInput"
          @keyup.enter="searchMovies"
          placeholder="search movie"
          type="text"
          class="p-2 rounded mr-2 text-black outline-none"
          required
        />
        <button
          v-if="searchResults.length > 0"
          @click="clearSearch"
          class="btn-first"
        >
          clear search
        </button>
      </div>
      <div v-if="noResult" class="text-3xl text-secondary">No Result</div>

      <div
        v-else
        class="
          grid grid-cols-1
          sm:grid-cols-2
          md:grid-cols-3
          lg:grid-cols-4
          gap-8
          py-4
        "
        id="movies"
      >
        <movie-card
          v-for="movie in searchResults.length > 0 ? searchResults : movies"
          :key="movie.id"
          :voteAvarage="movie.vote_average"
          :posterPath="movie.poster_path"
          :title="movie.title"
          :releaseDate="movie.release_date"
          :movieId="movie.id"
          :overview="movie.overview"
        >
        </movie-card>
      </div>
    </div>
    <div class="container mx-auto px-4 md:px-0 flex justify-center items-center h-96" v-else>
        <img src="@/assets/images/loader.svg" alt="">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      movies: [],
      searchResults: [],
      searchInput: '',
      noResult: false,
    }
  },
  methods: {
    async getMovies() {
      const movies = await this.$axios.get(
        `movie/now_playing?api_key=fa61e6fa7724edd99048bc5f0b11ae72&page=1`
      )
      this.movies = movies.data.results
    },
    async searchMovies() {
      if (this.searchInput.length > 0) {
        const result = await this.$axios.get(
          `search/movie?api_key=fa61e6fa7724edd99048bc5f0b11ae72&language=en-US&query=${this.searchInput}&page=1`
        )
        this.searchResults = result.data.results
        this.noResult = this.searchResults.length === 0
      }
    },
    clearSearch() {
      this.searchInput = ''
      this.searchResults = []
      this.noResult = false
    },
  },
  async fetch() {
    await this.getMovies()
  },
  fetchDelay : 1000,
}
</script>
