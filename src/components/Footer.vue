<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" v-model="checked" />
      <!--绑定计算属性-->
    </label>
    <span>已完成{{ finished }}件/总计{{todoList.length}}件</span>
    <button class="btn btn-warning" style="..." @click="del">清除已完成任务</button>
  </div>
</template>

<script setup>
import {inject,computed,unref} from 'vue'
const todoList = inject('todoList');
const selectAll = inject('selectAll');
const delFinished = inject('delFinished');
const del = () =>{
    if(window.confirm('确定删除吗')){
        delFinished();
    }
};
const finished = computed(()=>{
    return todoList.filter((item) => {return item.finished}).length;
});
const checked = computed({
    get(){
        return finished == todoList.length&&this.todoList.length>0;
    },
    set(value){
        selectAll(value);

    }
})


</script>

<style scoped>
.todo-footer{
    height: 40px;
    line-height: 40px;
    padding-left: 6px;
    margin-top: 5px;
}
.todo-footer label{
    display: inline-block;
    margin-right: 20px;
    cursor: pointer;
}
.todo-footer label input{
    position: relative;
    top:-1px;
    vertical-align: middle;
}
.todo-footer button{
    float: right;
    margin-top: 5px;
}
</style>