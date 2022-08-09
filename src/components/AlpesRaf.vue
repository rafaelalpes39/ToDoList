<template>
  <div>
    <div v-for="leafs in leafs" v-bind:key="leafs.id"  > 
  <LeaItem :leafs="leafs"  v-on:drop-todo="$emit('drop-todo',leafs.id)" />
  
  </div>
    </div>
 
</template>

<script>
import LeaItem from './LeaItem.vue'
export default ({
   name:'AlpesRaf', 
   components:{
    LeaItem
   }, 
   props:["leafs"]
})
</script>

<style scoped>

</style>