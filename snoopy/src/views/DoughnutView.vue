<template>
  <h1>Doughnut Graph</h1>
  <div>
    <Doughnut id="doughnut" 
              v-if="loaded" 
              :data=chartData 
              :options=chartOptions />
  </div>
</template>

<script>
import { Doughnut } from 'vue-chartjs'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'

ChartJS.register(ArcElement, Tooltip, Legend)

const URL = 'https://data.cityofnewyork.us/resource/7z8d-msnt.json'

export default {
  name: 'Doughnut',
  components: { Doughnut },
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
      required: true
    }
  },
  data() {
    return {
      loaded: false,
      chartData: {
        datasets: [{
          data: chartData
        }]
      }
    }
  },
  async mounted() {
  try {
    let response = await fetch(URL)
    chartData = await response.json()
    console.log(data)
    this.loaded = true
  } catch (e) {
    console.error(e)
  }
}
}
</script>