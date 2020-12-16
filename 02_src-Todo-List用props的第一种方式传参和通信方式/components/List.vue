<template>
   <ul class="todo-main">
     <Item v-for="(todo, index) in todos" :key="todo.id" :TodoCheck='TodoCheck' :todo='todo' :index='index' :TodoDev='TodoDev'></Item>
   </ul>
</template>

<script>
import Item from '@/components/Item';
export default {
  name: '',
  components:{
    Item
  },
  props:['todos','TodoCheck','TodoDev'],
}
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}

</style>
