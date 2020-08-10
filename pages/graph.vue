<template>
  <!--<bar-chart></bar-chart>-->
  <!--<graph-chart></graph-chart>-->

  <d3-network-graph :graph="graphSetup"></d3-network-graph>




</template>

<script>

  import BarChart from "../components/barChart";
  import GraphChart from "../components/graphChart";
  import D3NetworkGraph from "../components/d3NetworkGraph";


  export default {
    name: "graph",
    components: {D3NetworkGraph, GraphChart, BarChart},
    data() {
      return {
        graphSetup:{
          //panel
          restWidth: 5,

          nodes: [
            {id: 1, name: 'my node 1'},
            {id: 2, name: 'my node 2'},
            {id: 3, _color: 'orange'},
            {id: 4},
            {id: 5},
            {id: 6},
            {id: 7},
            {id: 8},
            {id: 9}
          ],
          links: [
            {sid: 1, tid: 2, _color: 'red'},
            {sid: 2, tid: 8, _color: 'f0f'},
            {sid: 3, tid: 4, _color: 'rebeccapurple'},
            {sid: 4, tid: 5, _color: 'black'},
            {sid: 5, tid: 6, _color: 'black'},
            {sid: 7, tid: 8, _color: 'black'},
            {sid: 5, tid: 8, _color: 'black'},
            {sid: 3, tid: 8, _color: 'black'},
            {sid: 7, tid: 9, _color: 'black'}
          ],
          options:
            {
              force: 3000,
              nodeSize: 20,
              nodeLabels: true,
              linkWidth: this.restWidth,
            }
        }
      }
    }
  }
</script>

<style scoped>

</style>
