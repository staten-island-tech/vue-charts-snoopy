<template>
  <h1>Doughnut Graph - Enrollment Average</h1>
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
        labels: [
          'District 1', 'District 2', 'District 3', 'District 4', 'District 5',
          'District 6', 'District 7', 'District 8', 'District 9', 'District 10',
          'District 11', 'District 12', 'District 13', 'District 14', 'District 15',
          'District 16', 'District 17', 'District 18', 'District 19', 'District 20',
          'District 21', 'District 22', 'District 23', 'District 24', 'District 25',
          'District 26', 'District 27', 'District 29', 'District 30', 'District 30',
          'District 31', 'District 32',
        ],
        datasets: [{ data: [] }]
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: true,
        backgroundColor: ['#caf0f8', '#ADD8f9']
      }
    }
  },
async mounted() {
    try {
      const res = await fetch('https://data.cityofnewyork.us/resource/7z8d-msnt.json')
      let data = await res.json()
      
      for (let i=0; i<32; i++) {
        this.chartData.datasets[0].data.push(data[i].ytd_enrollment_avg_)
      }

      this.loaded = true
    } catch (e) {
      console.error(e)
    }
    console.log(this.chartData)
  }
}

</script>