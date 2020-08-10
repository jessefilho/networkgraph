<template>
  <div id="app">
    <canvas id="planet-chart"></canvas>
  </div>
</template>

<script>
  //https://www.digitalocean.com/community/tutorials/vuejs-vue-chart-js
  import Chart from 'chart.js';
  import planetChartData from '../assets/chart-data';

  export default {
    name: "barChart",
    data() {
      return {
        planetChartData: planetChartData,
      }
    },
    methods: {
      createChart(chartId, chartData) {
        const ctx = document.getElementById(chartId);
        const myChart = new Chart(ctx, {
          type: chartData.type,
          data: chartData.data,
          options: chartData.options,
        });
      }
    },
    mounted() {
      this.createChart('planet-chart', this.planetChartData);
    }
  }
</script>

<style scoped>

</style>
