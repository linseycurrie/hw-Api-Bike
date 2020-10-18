<template>

<div class="row map">

    <l-map v-if="networks"
        :zoom="zoom" :center="center">
      <l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
      <l-marker v-if="selectedNetwork" class="marker"
        :lat-lng="latLng(selectedNetwork.location.latitude, selectedNetwork.location.longitude)">
        <l-icon class="lrgBike" :icon-size="largeIcon" :icon-url="icon"></l-icon>

      
      
      ></l-marker>>  


      <!-- <l-marker class="marker"
            v-for="(bike, index) in networks" :key="index"
            :lat-lng="latLng(bike.location.latitude, bike.location.longitude)" >
            <l-icon class="lrgBike" v-if="bike == selectedNetwork" :icon-size="largeIcon" :icon-url="icon"/>
            <l-icon class="normalBike" v-else :icon-size="normalIcon" :icon-url="icon"/>
        </l-marker> -->

    </l-map>

</div>
  
</template>


<script>
import { LMap, LTileLayer, LMarker, LIcon } from 'vue2-leaflet';
import Bike from '../assets/woman-biking.png'
import { eventBus } from '../main'

export default {
    name: "map-network",
    props:['networks', 'selectedNetwork'],
    data() {
        return {
        zoom:5,
        center: L.latLng(53.528881, -2.036170),
        currentZoom: 5,
        currentCenter: L.latLng(53.528881, -2.036170),
        url:'https://tile.thunderforest.com/transport/{z}/{x}/{y}.png?apikey=02874bea11474c4c8f8ed1de617533f2',
        attribution:'&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
        marker: L.latLng(53.528881, -2.036170),
        icon: Bike,
        iconSize: [30,30],
        normalIcon: [30, 30],
        largeIcon: [100, 100]
        }
    },

    components: {
        LMap,
        LTileLayer,
        LMarker,
        LIcon,
    },

        computed:{

       
           
    },

    methods: {
        latLng: function(lat, lng){
            return L.latLng(lat, lng);
        },

        updateCenter: function(center){
            this.currentCenter = center;
        },

        updateZoom: function(zoom){
            this.currentZoom = zoom;
        },
        
    }
}


</script>
<style>

 .map{
     height: 95vh;
 }

 .lrgBike{
     border: 1px solid black ;
     
 }

</style>