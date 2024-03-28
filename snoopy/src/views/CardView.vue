<template>
  <h1>New York City Districts Information</h1>
  <div class="card">
    <DistrictCard 
    v-for="district in data" 
    :District = "district"
    />
  </div>
</template>

<script setup>

import { ref, onMounted } from 'vue'
import DistrictCard from '../components/DistrictCard.vue'

const data = ref('')
async function getDistrict() {
  let res = await fetch('https://data.cityofnewyork.us/resource/7z8d-msnt.json')
  data.value = await res.json()
}
onMounted(() => {
  getDistrict()
})

console.log(data)

</script>

<style scoped>
h1 {
  align-items: center;
  margin-top: 80px;
}
</style>