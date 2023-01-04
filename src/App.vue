<script setup>
import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <nav>
    <RouterLink to="/" class="text-bold">Home</RouterLink>
    <RouterLink to="/about" class="ml-4 text-green-500">About</RouterLink>
  </nav>
  <hr>

  <RouterView />
</template>

<style scoped>

</style>
