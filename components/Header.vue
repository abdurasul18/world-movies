<template>
  <header>
    <div class="hero bg-no-repeat bg-cover bg-bottom py-2 relative">
      <div class="container mx-auto px-4 md:px-0">
        <div class="text-white relative z-10 pt-52 ">
          <h3 class="text-secondary  sm:text-xl md:text-3xl uppercase">Now Streaming</h3>
          <h1 class=" py-3 uppercase text-2xl md:text-7xl">
            <span class="font-bold"> Now </span> Streaming
          </h1>
          <a href="#movies" class="btn-first mt-5"> View Movies </a>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {}
</script>

<style scoped>
.hero {
  background-image: url('@/assets/images/movie-bg.jpg');
  height: 80vh;
}
.hero::after {
  content: '';
  background: rgba(0, 0, 0, 0.6);
  position: absolute;
  inset: 0;
}
</style>