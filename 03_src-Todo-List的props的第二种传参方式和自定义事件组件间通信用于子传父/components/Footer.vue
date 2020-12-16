<template>
  <div class="todo-footer">
    <label>
       <input type="checkbox" v-model="checkAll"/>
     </label>
    <span>
      <span>已完成{{finshed}}</span> / 全部{{Total}}
     </span>
    <button class="btn btn-danger" @click="clear">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: '',
  props:{
    todos:Array
  },
  methods:{
    clear(){
      this.$emit('todoClear')
    }
  },
  computed:{
    Total(){
      return this.todos.length
    },
    finshed(){
      return this.todos.reduce((prev,item)=>{
        if(item.isdone){
          prev += 1
        }
        return prev
      },0)
    },
    checkAll:{
      get(){
        return this.Total === this.finshed && this.finshed>0
      },
      set(val){
        this.$emit('todoCheckAll',val)
      }
    }
  }
}
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}


</style>
