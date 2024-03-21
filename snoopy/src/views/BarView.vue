<template>
<h1>Bar Graph</h1>
  <div class="container">
    <Bar v-if="loaded" :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  props: {
    chartOptions: {
        type: Object,
        required: true,
        default: () => ({
            responsive: true
        })
    }
  },
  chartData: {
    type: Object,
    required: true,
  },
  data () {
    return {
        loaded: false,
        chartData: {
            labels: ['Attendance'],
            datasets: [{label: 'district', data: [90] }],
        }
    }
  },
  async mounted () {
    this.loaded = false

    try {
      const { userlist } = await fetch('https://data.cityofnewyork.us/resource/7z8d-msnt.json')
      this.chartdata = userlist

      this.loaded = true
    } catch (e) {
      console.error(e)
    }
    console.log(this.chartData)
  }
}
</script>

<style scoped>

</style>