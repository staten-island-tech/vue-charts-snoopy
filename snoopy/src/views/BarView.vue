<template>
<h1>Attendance Average (%) of Districts 1 to 35 in New York City</h1>
  <div class="container">
    <Bar v-if="loaded" :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarView',
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
            labels: ['85-87', '87-89', '89-91', '91-93', '93-95'],
            datasets: [{label: ['Amount per Interval'], data: [] }],
        },
        chartOptions: {
            responsive: true,
            maintainAspectRatio: true,
            backgroundColor: ['rgb(111,123,266)', 'rgb(80,50, 230)','rgb(40,60, 200)']
        } 
    }
},
async mounted() {
    try {
      const res = await fetch('https://data.cityofnewyork.us/resource/7z8d-msnt.json')
      let data = await res.json()

      const one = data.filter((district) => 85 < district.ytd_attendance_avg_ && district.ytd_attendance_avg_ <= 87)
      this.chartData.datasets[0].data.push(one.length)
      const two = data.filter((district) => 87 < district.ytd_attendance_avg_ && district.ytd_attendance_avg_ <= 89)
      this.chartData.datasets[0].data.push(two.length)
      const three = data.filter((district) => 89 < district.ytd_attendance_avg_ && district.ytd_attendance_avg_ <= 91)
      this.chartData.datasets[0].data.push(three.length)
      const four = data.filter((district) => 91 < district.ytd_attendance_avg_ && district.ytd_attendance_avg_ <= 93)
      this.chartData.datasets[0].data.push(four.length)
      const five = data.filter((district) => 93 < district.ytd_attendance_avg_ && district.ytd_attendance_avg_ <= 95)
      this.chartData.datasets[0].data.push(five.length)

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