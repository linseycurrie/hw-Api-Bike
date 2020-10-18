<template>
  <div>
      <h3>Name Of Company: </h3>
      <h4>{{selectedNetwork.name}}</h4>

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