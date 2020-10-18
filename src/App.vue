<template>
<div id="app">
  <h1>City Bikes</h1>
  <img id="cityBike" src="./assets/Melbourne_City_Bikes.jpeg" alt="">

    <network-list :networks="networks"></network-list>
    
    <network :selectedNetwork="selectedNetwork"></network>
    <map-network :networks="networks" :selectedNetwork="selectedNetwork"></map-network>


  </div>
</template>

<script>
import Network from './components/Network.vue'
import MapNetwork from './components/MapNetwork.vue'
import NetworkList from './components/NetworkList.vue'
import { eventBus } from './main'

export default {
  name: 'App',

  data(){
    return{
      selectedNetwork: null,
      networks: [],
      networkIds: []


    }
  },
  components: {
    'network-list': NetworkList,
    'network': Network,
    'map-network': MapNetwork
    
  },

    computed: {
      getNetworkId(){
        this.networkIds = this.networks.map(network => network.id)
        return this.networkIds
      },
    },

  methods: {
      getNetworks: function() {
        fetch("http://api.citybik.es/v2/networks")
        .then(res => res.json())
        .then(data => this.networks = data.networks)

    },

    //   getNetworkId: function(){
    //     this.networkIds = this.networks.map(network => network.id)
    //     return this.networkIds
    // },


  },

  

  mounted() {
    this.getNetworks();

    // this.getNetworkId();

    eventBus.$on('selected-network', (network) => (this.selectedNetwork = network));
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
  background-color: aqua;
}



#cityBike{
  height: 150px;
  margin-left: 20px;
}
</style>
