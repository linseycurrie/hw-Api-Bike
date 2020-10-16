<template>
    <div>
        <label for="network_select">Please Select A Country</label>
        <select id="network_select" v-model="selectedNetwork" v-on:change="handleChange" @mouseover="">
            <option value="" disabled>Select A Network</option>
            <option v-for="(network, index) in networks" :key="index" :value="network">{{ network.location.city }}</option>
        </select>
    </div>
</template>

<script>
import NetworkList from './NetworkList.vue'
import { eventBus } from '../main'

export default {
    name: 'network-list',
    props: ['networks'],

    data(){
        return{
            selectedNetwork: null
        }
    },

    methods: {
        handleChange(){
            eventBus.$emit('selected-network', this.selectedNetwork)
        }
    }

    
}
</script>

<style>

</style>