<template>
<div id="app">

    <network-list :networks="networks"></network-list>
    <map-network :networks="networks"></map-network>


  </div>
</template>

<script>
import MapNetwork from './components/MapNetwork.vue'
import NetworkList from './components/NetworkList.vue'
import { eventBus } from './main'

export default {
  name: 'App',

  data(){
    return{
      selectedNetwork: null,
      networks: [],


    }
  },
  components: {
    'network-list': NetworkList,
    'map-network': MapNetwork
    
  },

  methods: {
      getNetworks: function() {
        fetch("http://api.citybik.es/v2/networks")
        .then(res => res.json())
        .then(data => this.networks = data.networks)
    }
  },

  mounted() {
    this.getNetworks();

    eventBus.$on('selected-network', (network) => {
      this.selectedNetwork = network
    })
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
