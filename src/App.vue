<script setup>
  import { RouterView } from "vue-router";
import AppHeader from "./components/AppHeader.vue";
import AppFooter from "./components/AppFooter.vue";
</script>

<template>
  <header>
    <AppHeader/>
  </header>
  
  <main class="mt-[10vh]">
    <RouterView/>
  </main>

  <footer>
    <AppFooter/>
  </footer>
</template>

<style scoped>
  
</style>