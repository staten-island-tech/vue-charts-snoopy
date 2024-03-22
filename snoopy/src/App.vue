<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Doughnut Graph</RouterLink>
        <RouterLink to="/card">Data</RouterLink>
        <RouterLink to="/bar">Bar Graph</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

</style>
