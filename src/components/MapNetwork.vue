<template>

<div class="row map">
    <h2>Map</h2>
    <l-map :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker v-if="networks" class="marker"
            v-for="(bike, index) in networks" :key="index"
            :lat-lng="latLng(bike.location.latitude, bike.location.longitude)" >
        </l-marker>

        <!-- <l-marker v-if="selectedNetwork" :lat-lng="latLng(selectedNetwork.location.latitude, selectedNetwork.location.longtitude)">U+1F6B2</l-marker> -->
    </l-map>

    


</div>
  
</template>

<script>
import { LMap, LTileLayer, LMarker } from 'vue2-leaflet';

export default {
    name: "map-network",
    props:['networks', 'selectedNetwork'],
    data() {
        return {
        zoom:5,
        center: L.latLng(53.528881, -2.036170),
        url:'https://tile.thunderforest.com/transport/{z}/{x}/{y}.png?apikey=02874bea11474c4c8f8ed1de617533f2',
        attribution:'&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
        marker: L.latLng(53.528881, -2.036170)
        }
    },

    components: {
        LMap,
        LTileLayer,
        LMarker,
    },

    methods: {
        latLng: function(lat, lng){
            return L.latLng(lat, lng);
        },
        
    }
}


</script>
<style>

 .map{
     height: 95vh;
 }

 .marker{
     
 }

</style>