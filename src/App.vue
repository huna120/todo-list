<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header></Header>
      <List></List>
      <Footer></Footer>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import Footer from "./components/Footer.vue";
import {reactive,provide} from "vue";
export default {
name:"App",
setup(props){
  let todoList = reactive([
    {
      title:"打一场羽毛球",
      finished:true
    },
    {
      title:"打一场篮球",
      finished:false
    }
  ]);
  const del = (index) =>{
    if(window.confirm("你确定删除吗")){
      todoList.splice(index,1);
    }
  };
  const add = (obj) =>{
    todoList.unshift(obj);
  };
  const selectAll = isChecked =>{
    todoList.forEach((item) =>{
      item.finished = isChecked;
    });
  };
  const delFinished =() =>{
    for(let index = todoList.length-1;index>=0;index--){
      if(todoList[index].finished){
        todoList.splice(index,1);
      }
    }
  };
  provide('todoList',todoList);
  provide('del',del);
  provide('add',add);
  provide('selectAll',selectAll);
  provide('delFinished',delFinished);
  },
  components:{
    Header,
    List,
    Footer
  }

}
</script>

<style>


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
