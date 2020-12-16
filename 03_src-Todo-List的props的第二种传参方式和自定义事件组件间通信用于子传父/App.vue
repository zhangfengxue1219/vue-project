<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <!-- todoAdd为自定义事件通信方式 用于子传父元素-->
      <Header :todos='todos' @todoAdd='todoAdd'></Header>
      <List :todos='todos' :todoDev='todoDev' :todoCheck='todoCheck'></List>
      <Footer :todos='todos' @todoCheckAll='todoCheckAll' @todoClear='todoClear'></Footer>
    </div>
  </div>
</template>

<script>
import Header from '@/components/Header';
import List from '@/components/List';
import Footer from '@/components/Footer';
export default {
  name: '',
  components:{
    Header,
    List,
    Footer
  },
  data(){
    return{
      /* todos:[
        {id:'01',hobby:'游泳',isdone:false},
        {id:'02',hobby:'看演出',isdone:true},
      ] */
     todos:JSON.parse(localStorage.getItem('TodosKey'))||[]
    }
  },
  watch:{
    todos:{
      deep:true,
      handler(newVal,oldVal){
        localStorage.setItem('TodosKey',JSON.stringify(newVal))
      }
    }
  },
  methods:{
    /* 添加Item的方法 */
    todoAdd(obj){
      this.todos.unshift(obj)
    },
    /* 删除item的方法 */
    todoDev(index){
      this.todos.splice(index,1)
    },
    /* 点击单个复选框事件 */
    todoCheck(index){
      this.todos[index].isdone=!this.todos[index].isdone
    },
    /* 全选/全部选 */
    todoCheckAll(val){
      this.todos.forEach(item=>item.isdone=val)
    },
    /* 清除已完成任务 */
    todoClear(){
     this.todos = this.todos.filter(item=>!item.isdone)
    }
  }
}
</script>

<style scoped>
/*app*/
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
