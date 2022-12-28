<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper py-5">

      <nav class="w-96 mx-auto">
        <RouterLink class="bg-gray-700 text-white px-4 py-3 mr-3" to="/">Home</RouterLink>
        <RouterLink class="bg-gray-700 text-white px-4 py-3" to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

</style>
