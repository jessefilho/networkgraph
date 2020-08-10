<template>
  <b-row>
    <b-col>


      <b-row>
        <b-col>
          <d3-network :net-nodes="graph.nodes"
                      :net-links="graph.links"
                      :options="graph.options">
          </d3-network>
        </b-col>
      </b-row>


    </b-col>
  </b-row>

</template>

<script>
  //https://github.com/emiliorizzo/vue-d3-network
  import D3Network from 'vue-d3-network'
  export default {
    name: "d3NetworkGraph",
    props:['graph'],
    components: {
      D3Network
    }
  }
</script>

<style scoped>

</style>
