<template>
 <div class="todo-container">
    <div class="todo-wrap">
      <Header :todos='todos' :TodoAdd='TodoAdd'></Header>
      <List :todos='todos' :TodoCheck='TodoCheck' :TodoDev='TodoDev'></List>
      <Footer :todos='todos' :checkedAll='checkedAll' :clearTest='clearTest'></Footer>
    </div>
  </div>
</template>

<script>
import Header from '@/components/Header'
import List from '@/components/List'
import Footer from '@/components/Footer'
export default {
  name: '',
  components:{
      Header,
      List,
      Footer
  },
  data(){
      return{
        //   todos:[
        //       {id:'1',hobby:'漂流',isdone:true},
        //       {id:'2',hobby:'看电影',isdone:false},
        //       {id:'3',hobby:'打游戏',isdone:true},
        //   ]
        todos:JSON.parse(localStorage.getItem('TODOS_KEY')) || []
      }
  },
  watch:{
      todos:{
          //代表深度监视
          /* 
            一般监视和深度监视
            一般监视的是数组本身的数据，但是数组内部对象的数据是监视不到的
            深度监视可以监视到数组本身的数据，也可以监视到数组内部对象的数据
          */
         deep:true,
         handler(newVal,oldVal){
             /* 
                只要todos数据发生变化，就把变化的数据存储到localStarage当中
                localStarage是前端本地存储的方案，是一个小型的数据库，存储到localStarage
                当中的东西会自动转化为字符串
                localStarage有四个API
                localStarage.getItem('键',值)获取localStarage当中的某个数据，能获取到获取到，获取不到返回null,不影响其他
                localStarage.removeItem('键') 删除localStarage当中的某个数据
                localStarage.clear()清空localStarage当中的数据
                localStarage.setItem('键’)存储数据
             */
            /* 
                localStarage.setItem('TODOS_KEY',newVal)不能直接存储成对象数据类型，因为对象数据类型会转换为字符串[object  Object]'
            */
           localStorage.setItem('TODOS_KEY',JSON.stringify(newVal))
         }
      }
  },
  methods:{
      TodoAdd(obj){
          this.todos.unshift(obj)
      },
      TodoCheck(index){
          this.todos[index].isdone=!this.todos[index].isdone
      },
      TodoDev(index){
          this.todos.splice(index,1)
      },
      checkedAll(val){
          this.todos.forEach(item => {
              item.isdone = val
          })
      },
      clearTest(){
        this.todos = this.todos.filter(item=>!item.isdone)
        console.log(this.todos)
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
