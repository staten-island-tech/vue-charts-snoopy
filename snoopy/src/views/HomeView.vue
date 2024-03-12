<template>
  <div class="container">
    <Bar v-if="loaded" :data="chartData" />
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

const URL = 'https://data.cityofnewyork.us/resource/7z8d-msnt.json'

export default {
  name: 'BarChart',
  components: { Bar },
  data: () => ({
    loaded: false,
    chartData: null
  }),
  async mounted () {
    this.loaded = false

    try {
      const userlist = await fetch(URL).ytd_attendance_avg_
      this.chartData = userlist
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>