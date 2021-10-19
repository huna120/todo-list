<template>
  <div class="todo-header">
      <!--键盘松开的时候-->
      <input type="text" placeholder="请输入今日任务清单，回车键确认" @keyup.enter="addItem({title:title,finished:flase})" v-model="title" />
  </div>
</template>

<script setup>
import { inject,ref} from "vue";
let title = ref("");
const add = inject("add");
const addItem  = obj =>{
    if(!obj.title){
        alert("标题不能为空");
        return;
    }
    add(obj);
    title = "";
};
</script>

<style>
.todo-header input{
    width: 560px;
    height: 28px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 4px 7px;
    outline: none;
}
.todo-header input:focus{
    outline: none;
    border-color: rgba(255,0,0,0.8);
    box-shadow: inset 0 1px 1px rgba(255,0,0,0.075),0 0 8px,rgba(255,0,0,0.6);
}
</style>