<template>
  <div id="app">
  <HeaderTo />
  <AddComponents v-on:addNotes="Nnotes" />
  <AlpesRaf v-bind:leafs="leafs"  v-on:drop-todo="drop"/>
  </div>
</template>

<script>

import AlpesRaf from '../components/AlpesRaf';
import AddComponents from '../components/AddComponents.vue';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    AlpesRaf,
    AddComponents
},
  data(){
    return{
            leafs: []
          
          }
       },
methods:{
  drop(id){
    axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
    .then(res=>{
    this.leafs= this.leafs.filter( leafs => leafs.id !==id);
    return res
    })
    .catch(error=>{return Promise.reject(error);
    })
    
    //this.leafs= this.leafs.filter( leafs => leafs.id !==id);
  },
  Nnotes(newTodo){
    const{title, completed} = newTodo;
    axios.post('https://jsonplaceholder.typicode.com/todos',{
      title,
      completed
    })
    .then(alpes=>this.leafs = [...this.leafs,alpes.data])
    .catch(error=>{return Promise.reject(error);
    })
  }
},
created(){
  axios.get("https://jsonplaceholder.typicode.com/todos")
  .then(alpes=>this.leafs = alpes.data)
  .catch(error => {
    return Promise.reject (error)
  })
}


}
       

</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{

  font-family: Arial, Helvetica, sans-serif;
}

.btn{

  display: inline;
  border: none;
  background: #555;
  color:white;
  padding: 10px,  20px;
  cursor:pointer;
}
.btn:hover{
background:#666;
}
</style>
