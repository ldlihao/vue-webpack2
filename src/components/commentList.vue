<template>
  <div class="col-md-8">
    <h3 class="reply">评论回复：</h3>
    <h2 v-show="comments.length===0">暂无评论，点击左侧添加评论！！！</h2>
    <ul class="list-group">
      <!--向item中传递:comment="comment" 属性-->
      <commentItem v-for="(comment,index) in comments" :comment="comment"
                   :key="index" :delete-comment="deleteComment" ></commentItem>
    </ul>
  </div>
</template>
<script>
  import commentItem from './commentItem.vue';
  export default{
    //声明接收那些属性
      props:['comments','deleteComment'],//comments 值得是app data中的定义的 comments数组

    //将commentItem 映射成标签
    components: {
      commentItem
    }

  };
</script>
<style>
  .reply {
    margin-top: 0px;
  }

</style>
