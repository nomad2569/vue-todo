
<template>
  <div id="app">
    <TodoHeader/>
    <TodoInput @addTodoItem="addOneItem"></TodoInput>
    <TodoList :propsdata="todoItems" @removeItem="removeOneItem" @toggleItem="toggleItem"></TodoList>
    <TodoFooter @clearAll="clearAllItems"></TodoFooter>
  </div>
</template>

<script>
import TodoFooter from "./components/TodoFooter.vue"
import TodoHeader from "./components/TodoHeader.vue"
import TodoInput from "./components/TodoInput.vue"
import TodoList from "./components/TodoList.vue"

export default {
  data(){
    return{
      todoItems:[]
    }
  },
  methods:{
    addOneItem(todoItem){
      var obj = {
                    completed:false,
                    item:todoItem
                }
      localStorage.setItem(todoItem, JSON.stringify(obj))
      this.todoItems.push(obj)
    },
    removeOneItem(todoItem, index){
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index,1);
    },
    toggleItem(todoItem){
        todoItem.completed = !todoItem.completed
        localStorage.removeItem(todoItem.item)
        localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
    }
  },
  clearAllItems(){
    this.todoItems=[];
    localStorage.clear();
  },
  created(){
            for(var i = 0; i < localStorage.length; i++){
                if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
                    this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))))
                }
            }
    },
  name: 'App',
  components: {
    "TodoFooter" : TodoFooter,
    "TodoHeader" : TodoHeader,
    "TodoInput" : TodoInput,
    "TodoList" : TodoList,
  }
}
</script>

<style scoped>
</style>