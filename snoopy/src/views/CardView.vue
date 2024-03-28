<template>
  <select @change="FilterData(value)">
    <option value="0">All</option>
    <option value="1">District 1</option>
    <option value="2">District 2</option>
    <option value="3">District 3</option>
    <option value="4">District 4</option>
    <option value="5">District 5</option>
    <option value="6">District 6</option>
    <option value="7">District 7</option>
  </select>
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
const Data = ref('')

async function getDistrict() {
  let res = await fetch('https://data.cityofnewyork.us/resource/7z8d-msnt.json')
  Data.value = await res.json()
  data.value = Data
}
onMounted(() => {
  getDistrict()
})

console.log(data)

function FilterData(num) {
  data.value = Data.filter((district) => district===(num-1))
}

</script>

<style scoped>
h1 {
  align-items: center;
  margin-top: 80px;
}
</style>