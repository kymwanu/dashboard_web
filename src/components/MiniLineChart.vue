<script setup>
import { Line } from 'vue-chartjs'
import {
  Chart,
  LineElement,
  PointElement,
  LinearScale,
  Title,
  CategoryScale,
  Filler,
} from 'chart.js'

Chart.register(LineElement, PointElement, LinearScale, Title, CategoryScale, Filler)

defineProps({
  chartData: Object,
  chartOptions: Object,
})
</script>

<template>
  <Line :data="chartData" :options="chartOptions" />
</template>
