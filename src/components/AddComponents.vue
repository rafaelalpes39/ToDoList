<template>
    <div>
        <form @submit="Add">
            <input type="text" v-model="it" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
export default {
   name: 'AddComponent',
  
  data(){
    return{
        it:""
    }
  },
   methods:{
    Add(seaversitymabangis){
       seaversitymabangis.preventDefault();
        const newTodo = { 
         id: 0,
        title: this.it,
        completed: false 
        }
         this.$emit('addNotes',newTodo);
        this.it="";
    }
    }
   }

</script>

<style scoped>

form{
    display: flex;
}

input[type=text]{
    flex:10;
    padding: 5px;
}
input[type="button"]{
    flex:2;
    }

</style>
