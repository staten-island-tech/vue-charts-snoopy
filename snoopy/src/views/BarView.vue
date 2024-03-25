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
    },
    chartData: {
    type: Object,
    required: true,
    },
},
data () {
    return {
        loaded: false,
        chartData: {
            labels: ['1', '2', '3'],
            datasets: [{label: ['D1', 'D2'], data: [100, 90, 50] }],
        },
        chartOptions: {
            responsive: true,
            maintainAspectRatio: true,
            backgroundColor: ['rgb(111,123,266)', 'rgb(80,50, 230','rgb(40,60, 200']
        } 
    }
},
async mounted () {
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