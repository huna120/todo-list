<template>
  <ul class="todo-main">
      <item v-for="(item,index) in todoList" :key="index" :item="item"></item>
  </ul>
</template>

<script>
import Item from "./Item.vue";
import {inject} from 'vue';
export default {
name:'List',
setup(props){
    const todoList = inject('todoList');
    return{
        todoList
    }
},
components:{
    Item
}
}
</script>

<style scoped>
.todo-main{
    margin-left: 0px;
    border:1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
}
.todo-empty{
    height: 40px;
    line-height: 40px;
    border:1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-left: 10px;
}
</style>