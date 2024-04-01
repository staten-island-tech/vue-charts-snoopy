<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="https://www.cityguideny.com/uploads2/74888/NYC-DOE.jpg?ModPagespeed=off" />

    <div class="wrapper">
      <nav>
        <RouterLink to="/"> NYC School Districts Information </RouterLink>
        <RouterLink to="/percent"> Attendance Average </RouterLink>
        <RouterLink to="/enrollment"> Enrollment Average </RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
.logo {
  width: 280px;
  height: 225px;
}
</style>
