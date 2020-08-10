<template>
  <div>
    <div id="app">
      <canvas id="planet-chart"></canvas>
    </div>
    <button id="addNode" v-on:click="addNode">Add Node</button>
    <button id="removeNode">Remove Node</button>
    <button id="reset">Reset</button>
    <button id="relayout">Relayout</button>
  </div>
</template>

<script>
  import Chart from 'chart.js'
  import graphChart from 'chartjs-chart-graph'
  import miserablesChartData from '../assets/miserables-chart-data'

  import miserablesData from '../assets/data/miserables.json'

  export default {
    name: "graphChart",
    data() {
      return {
        miserablesData:miserablesData
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
      },
      loadGraph(data){
        console.log(data)
        let outgoingMap = new Map();

        data.nodes.forEach((n) => {
          const outgoing = data.links.filter((e) => e.source === n.id);
          outgoingMap.set(n.id, outgoing);
        });

        let sub = 3;
        let nodes = data.nodes.slice(0, data.nodes.length - sub);


        let labels = nodes.map((d) => d.id);
        let edges = nodes
          .reduce((acc, n) => acc.concat(outgoingMap.get(n.id)), [])
          .filter((d) => labels.indexOf(d.target) >= 0);

        let chartData = {
          type: 'forceDirectedGraph',
          data: {
            labels,
            datasets: [
              {
                pointBackgroundColor: 'steelblue',
                pointRadius: 5,
                data: nodes,
                edges,
              },
            ],
          },
          options: {
            simulation: {
              forces: {
                link: {
                  id: (d) => d.id,
                },
              },
            },
            legend: {
              display: false,
            },
          },
        };


        return chartData
      },

      addNode() {
        console.log('adding nodes...')

        let sub = 3;
        let data = this.miserablesData;
        let rest = data.nodes.slice(data.nodes.length - sub);
        if (rest.length === 0) {
          return;
        }
      }
    },
    mounted() {

      this.createChart('miserables-chart', this.loadGraph(this.miserablesData));




    }
  }
</script>

<style scoped>

</style>
