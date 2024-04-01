<template>
  <select @change="FilterData($event.target.value)">
    <option value=00>All</option>
    <option value=01>District 1</option>
    <option value=02>District 2</option>
    <option value=03>District 3</option>
    <option value=04>District 4</option>
    <option value=05>District 5</option>
    <option value=06>District 6</option>
    <option value=07>District 7</option>
    <option value=08>District 8</option>
    <option value=09>District 9</option>
    <option value=10>District 10</option>
    <option value=11>District 11</option>
    <option value=12>District 12</option>
    <option value=13>District 13</option>
    <option value=14>District 14</option>
    <option value=15>District 15</option>
    <option value=16>District 16</option>
    <option value=17>District 17</option>
    <option value=18>District 18</option>
    <option value=19>District 19</option>
    <option value=20>District 20</option>
    <option value=21>District 21</option>
    <option value=22>District 22</option>
    <option value=23>District 23</option>
    <option value=24>District 24</option>
    <option value=25>District 25</option>
    <option value=26>District 26</option>
    <option value=27>District 27</option>
    <option value=28>District 28</option>
    <option value=29>District 29</option>
    <option value=30>District 30</option>
    <option value=31>District 31</option>
    <option value=32>District 32</option>
    <option value=75>Special Ed District 75</option>
    <option value=ALT>Alternative High Schools</option>
    <option value=City>Citywide</option>
  </select>
  <h1>New York City Districts Information</h1>
  <div class="card">
    <DistrictCard 
    v-for="district in data"
    :District = "district"/>
  </div>
</template>

<script setup>

import { ref, onMounted } from 'vue'
import DistrictCard from '../components/DistrictCard.vue'

const Data = ref([])
const data = ref([])

async function getDistrict() {
  let res = await fetch('https://data.cityofnewyork.us/resource/7z8d-msnt.json')
  data.value = await res.json()
  Data.value = data.value
}
onMounted(() => {
  getDistrict()
})

function FilterData(value) {
  if (value === '00') {
    data.value = Data.value
  }
  else {
    data.value = Data.value.filter(el => el.district.includes(value)) 
  }
}

</script>

<style scoped>

  
</style>