<template>
   <div class="todo-container">
    <div class="todo-wrap">
      <Header :todos='todos' :todoAdd='todoAdd'></Header>
      <List :todos='todos' :todosDev='todosDev' :todoCheck='todoCheck'></List>
      <Footer :todos='todos' @todosCheckAll='todosCheckAll' @todosClear='todosClear'></Footer>
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
        {id:'1',hobby:'骑马',isOk:true},
        {id:'2',hobby:'射箭',isOk:false},
      ] */
      todos:JSON.parse(localStorage.getItem('TODOS'))||[]
    }
  },
  watch:{
    todos:{
      deep:true,
      handler(newVal,oldVal){
        localStorage.setItem('TODO',JSON.stringify(newVal))
      }
    }
  },
  methods:{
    todosDev(index){
      this.todos.splice(index,1)
    },
    todoCheck(index){
      this.todos[index].isOk=!this.todos[index].isOk
    },
    todoAdd(obj){
      this.todos.unshift(obj)
    },
    todosCheckAll(val){
      this.todos.forEach(item=>item.isOk=val)
    },
    todosClear(){
      this.todos = this.todos.filter(item=>!item.isOk)
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
