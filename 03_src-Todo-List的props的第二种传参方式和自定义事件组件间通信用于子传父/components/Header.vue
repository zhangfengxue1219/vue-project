<template>
  <div class="todo-header">
    <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="hobby" @keyup.enter="add"/>
  </div>
</template>

<script>
export default {
  name: '',
  props:{
      todos:Array
  },
  data(){
      return{
          hobby:''
      }
  },
  methods:{
      add(){
          const hobby = this.hobby
          if(hobby.trim()){
              const id = Date.now()
              const isdone = false
              let obj = {
                  id,
                  hobby,
                  isdone
              }
              /* 自定义事件通信方式接收参数，用于子传父元素 */
              this.$emit('todoAdd',obj)
          }else{
              alert('请输入合法内容')
          }
          this.hobby=''
      }
  }
}
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
}

</style>
