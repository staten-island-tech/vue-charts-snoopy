<template>
  <h1>hi</h1>
  <div class="card">
    <DistrictCard v-for="district in data" :District = district></DistrictCard>
  </div>
</template>

<script setup>
import DistrictCard from '@/components/DistrictCard.vue';
const URL = 'https://data.cityofnewyork.us/resource/7z8d-msnt.json'
let data = ''

async function mounted() {
    try {
      let response = await fetch(URL)
      data = await response.json()
      console.log(data)
    } catch (e) {
      console.error(e)
    }
  }

mounted()
</script>

<style scoped>

</style>