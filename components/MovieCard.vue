<template>
  <div class="movie-card relative">
    <span class="badge"> {{ voteAvarage }} </span>
    <div class="movie-img relative">
      <img
        :src="`https://image.tmdb.org/t/p/w500/${posterPath}`"
        :alt="title"
        class="w-full"
      />
      <div class="description text-white bg-secondary absolute font-mona p-4">
       {{ overview }}
      </div>
    </div>
    <div class="card-info text-gray-200">
      <div class="title text-2xl">
        {{ title.slice(0, 25) }}
        <span v-if="title.length > 25"> ... </span>
      </div>
      <div class="realised text-xl">
        {{
          new Date(releaseDate).toLocaleString('en-US', {
            year: 'numeric',
            month: 'long',
            day: 'numeric',
          })
        }}
      </div>
      <nuxt-link class="btn-second my-2" :to="`/movies/${movieId}`">
        Get More Info
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  props: ['voteAvarage', 'posterPath', 'title', 'releaseDate', 'movieId', 'overview'],
}
</script>

<style scoped>
.movie-img {
    overflow: hidden;
    min-height: 395px;
}
.movie-img:hover .description {
    bottom: 0;
}
.description {
    bottom: -100%;
    transition: all ease 0.7s;
}
</style>