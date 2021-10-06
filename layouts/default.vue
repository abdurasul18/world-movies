<template>
  <div class="app min-h-screen  bg-primary font-mona">
    <Nuxt keep-alive/>
  </div>
</template>

<script>
export default {}
</script>

<style>
.btn-first {
    @apply w-32  rounded-md bg-secondary text-white p-2 flex justify-center hover:bg-opacity-80
}
.badge {
    @apply absolute top-0 left-0 bg-secondary rounded-br-2xl w-9 h-9 flex items-center justify-center text-white font-bold
}
.btn-second {
    @apply w-32  rounded-md  text-white p-2 flex justify-center hover:bg-secondary duration-75 border-secondary rounded-md border 
}
* {
    scroll-behavior: smooth;
}
</style>