<template>
  <div class="flex-container" v-if="selectedNetwork">
      <h3>Name Of Company:  {{selectedNetwork.name}} </h3>
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

.flex-container{
  display: flex;
  direction: row;
  justify-content: center;
}

</style>