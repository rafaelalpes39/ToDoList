<template>
    
    <header class="header"> <h1> Todo List</h1></header>

     <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
</template>

<script>


export default {
  name:'HeaderTo'
}
</script>

<style scoped>
.header{

  background:teal;
  color:white;
  text-align: center;
  padding:2px;
}

</style>
