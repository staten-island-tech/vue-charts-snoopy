<template>
  <h1>Doughnut Graph</h1>
  <div class="container">
    <Doughnut v-if="loaded" :data="data" />
  </div>
</template>

<script>
import { Doughnut } from 'vue-chartjs'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'

ChartJS.register(ArcElement, Tooltip, Legend)
let loaded = false
const URL = 'https://data.cityofnewyork.us/resource/7z8d-msnt.json'
let response = await fetch(URL)
const data = await response.json()

export default {
  name: 'App',
  components: {
    Doughnut
  },
  data() {
    loaded = true
  }
}
</script>