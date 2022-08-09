<template>

    <div class="Todo-item" v-bind:class="{'is-completed':leafs.completed}">
      
        <p>
            
           <input type="checkbox" v-on:change="done" v-bind:checked="leafs.completed">
             {{ leafs.title }}
           <button class="del" v-on:click="$emit('drop-todo', leafs.id)">DELETE</button>
             </p>
    </div>
</template>

<script> 

export default{
    name:"LeaItem",
   props:["leafs"],
      data() {
    return {
      todos: this.leafs,
    }
  },
  methods: {
    done() {
      this.todos.completed =! this.todos.completed;
    },
  },
   }

</script>


<style scoped>

.Todo-item{
    background:#f4f4f4;
    padding:10px;
    border-bottom:1px#ccc dotted
}

.is-completed{

    text-decoration: line-through;
}
.del{
background: red;
color:#fff;
float:right;
border:none;
padding:3px 9px;
border-radius:50px;
cursor:poiner;
}
</style>