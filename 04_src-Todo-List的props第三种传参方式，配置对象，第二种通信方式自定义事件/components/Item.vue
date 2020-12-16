<template>
   <li @mouseenter="isShow=true" @mouseleave="isShow=false" :class='{myColor:isShow}'>
    <label>
      <input type="checkbox" :checked='todo.isOk' @click="checkOne"/>
      <span>{{todo.hobby}}</span>
    </label>
    <button class="btn btn-danger" @click='dec' v-show="isShow">删除</button>
   </li>
</template>

<script>
export default {
  name: '',
  props:{
    /* 第三种传参方式，为一个配置对象 */
    todo:{
      type:Object,
      require:true
    },
    index:{
      type:Number,
      default:0
    },
    todosDev:{
      type:Function,
      require:true
    },
    todoCheck:{
      type:Function,
      require:true
    }
  },
  data(){
    return{
      isShow:false
    }
  },
  methods:{
    dec(){
      const {hobby}=this.todo
      if(confirm(`你确定要删除${hobby}吗？`)){
        this.todosDev(this.index)

      }else{
        alert('请输入合法数据')
      }
    },
    checkOne(){
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
