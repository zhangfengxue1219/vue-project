<template>
   <div class="col-md-8">
        <h3 class="reply">评论回复：</h3>
        <h2 style='display: none'>暂无评论，点击左侧添加评论！！！</h2>
        <ul class="list-group">
            <Item v-for="(commite, index) in commites" :key="commite.id" :commite='commite' :index='index' :Devmethod='Devmethod'></Item>
        </ul>
      </div>
</template>

<script>
import Item from '@/components/Item'
export default {
  name: '',
  components:{
      Item
  },
  props:['commites','Devmethod']
}
</script>

<style scoped>
    .reply {
  margin-top: 0px;
}
</style>
