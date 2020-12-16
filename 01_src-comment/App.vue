<template>
   <div>
       <Header></Header>
    <div class="container">
        <Add :Addmethod='Addmethod'></Add>
        <List :commites='commites' :Devmethod='Devmethod'></List>
    </div>
  </div>
</template>

<script>
import Header from '@/components/Header'
import Add from '@/components/Add'
import List from '@/components/List'
export default {
  name: '',
  components:{
      Header,
      Add,
      List
  },
  data(){
      return{
          commites:[
              {id:'1',username:'朱允炆',content:'胜败乃兵家常事'},
              {id:'2',username:'小河公主',content:'我来自西域'},
              {id:'3',username:'上官公',content:'胜利是属于我们的'},
              {id:'4',username:'秦晖',content:'哎i哎'},
          ]
      }
  },
  methods:{
      Addmethod(msg){
          this.commites.unshift(msg)
      },
      Devmethod(index){
          this.commites.splice(index,1)
      }
  }
}
</script>

<style scoped>

</style>
