<template>
  <div>
      <h3>Name Of Company: {{selectedNetwork.name}}</h3>
      
  </div>
</template>

<script>
import Network from './Network.vue'

export default {
    name: 'network',
    props: ['selectedNetwork']

        }
</script>

<style>

</style>