<template>
  <h1>New York City Districts 1 to 35 Information</h1>
  <div id="chart"></div>
  <div class="card">
    <DistrictCard 
    v-for="district in district" 
    :key = "district"
    :ytd_attendance_avg_="district.ytd_attendance_avg_"
    :ytd_enrollment_avg_="district.ytd_enrollment_avg_"
    />
  </div>
</template>

<script setup>
// import DistrictCard from '@/components/DistrictCard.vue';
// const URL = 'https://data.cityofnewyork.us/resource/7z8d-msnt.json'
// let data = ''
// import { createApp } from 'vue'
// import App from './DoughnutView.vue';

// // function onBeforeMount(callback: () => void): void

// async function mounted() {
//   try {
//     let response = await fetch(URL)
//     data = await response.json()
//     console.log(data)
//   } catch (e) {
//     console.error(e)
//   }
// }
// mounted()

// createApp(App).mount('#chart')


import { ref, onMounted } from 'vue'
import DistrictCard from '../components/DistrictCard.vue'

const district = ref('')
async function getDistrict() {
  let res = await fetch('https://data.cityofnewyork.us/resource/7z8d-msnt.json')
  let data = await res.json()
  district.value = data
}
onMounted(() => {
  getDistrict()
})



</script>

<style scoped>
h1 {
  align-items: center;
  margin-top: 80px;
}
</style>