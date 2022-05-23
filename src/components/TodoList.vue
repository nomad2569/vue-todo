<template>
  <div>
      <ul>
          <li v-for="(todoItem, index) in propsdata" :key="todoItem">
              <i class="fas fa-check" :class="{checkBtnCompleted : todoItem.completed}" @click="toggleComplete(todoItem,index)"></i>
              <span :class="{checkBtnCompleted : todoItem.completed}">{{todoItem.item}}</span>
              <i class="fas fa-trash-alt" @click="removeItem(todoItem)"></i>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
    props:['propsdata'],
    methods:{
      removeItem(todoItem, index){
          this.$emit('removeItem', todoItem, index)
      },
      toggleComplete(todoItem){
          this.$emit("toggleItem", todoItem)
          
      }
    },
    
}
</script>

<style>
.checkBtnCompleted{
    color:red;
    text-decoration: line-through;
}
</style>