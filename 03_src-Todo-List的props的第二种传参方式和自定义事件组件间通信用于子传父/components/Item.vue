<template>
  <li @mouseenter="isShow=true" @mouseleave="isShow=false" :class='{myColor:isShow}'>
    <label>
      <input type="checkbox" :checked='todo.isdone' @click="checkedone"/>
      <span>{{todo.hobby}}</span>
    </label>
    <button class="btn btn-danger" v-show="isShow" @click='dev'>删除</button>
  </li>
</template>

<script>
export default {
  name: '',
  props:{
    todo:Object,
    index:Number,
    todoDev:Function,
    todoCheck:Function
  },
  data(){
    return{
      isShow:false
    }
  },
  methods:{
    dev(index){
      const {hobby} = this.todo
      if(confirm(`你确认删除${hobby}吗？`)){
        this.todoDev(this.index)
      }
    },
    checkedone(index){
      this.todoCheck(this.index)
    }
  }
}
</script>

<style scoped>
/*item*/
.myColor{
  background: #ccc;
}
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
 /*  display: none; */
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}

</style>
