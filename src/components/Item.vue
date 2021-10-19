<template>
  <li @mouseenter="change(true)" @mouseleave="change(false)">
      <label>
          <input type="checkbox" v-model="item.finished">
          <span>{{item.title}}</span>
      </label>
      &nbsp;<button class="btn btn-warning" v-show="isShow" @click="delItem('{{item.index}}')">删除</button>
  </li>
</template>

<script>
import {inject,ref} from 'vue';
export default {
name:'Item',
setup(props){
    let isShow = ref(false);
    const change = (show) => {
        isShow = show;
    }
    const delItem = inject('del');
    return{
        isShow,change,delItem
    };
},
props:{
    item:Object
}
}
</script>

<style scoped>
li{
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom:1px solid #ddd;
}
li label{
    float: left;
    cursor: pointer;
}
li label li input{
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
}
li button{
    float: right;
    margin-top: 3px;
}
li:before{
    content: initial;
}
li:last-child{
    border-bottom: none;
}
</style>