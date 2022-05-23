<template>
  <div>
      <input type="text" v-model="newTodo" @keyup.enter="addTodo"/>
      <button @click="addTodo">
          add
      </button>
  </div>
</template>

<script>
export default {
    data(){
        return{
            newTodo:""
        }
    },
    methods:{
        addTodo(){
            if(this.newTodo !== ''){
                this.$emit('addTodoItem', this.newTodo)
               this.newTodo = ""
            }
        }
    }
}
</script>

<style>

</style>