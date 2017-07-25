<template>
  <div>
    <header class="site-header jumbotron">
      <div class="container">
        <div class="row">
          <div class="col-xs-12">
            <h1>请发表对React的评论</h1>
          </div>
        </div>
      </div>
    </header>
    <div class="container">
      <comment-add :add-comment="addComment"></comment-add>
      <commentList :comments="comments" :delete-comment="deleteComment"></commentList>
    </div>
  </div>
</template>
<script>
  import commentAdd from './commentAdd.vue';
  import commentList from './commentList.vue';
  export default{
    data () {
      return{
        comments:[] //定义空数组 使用 created 方法来模拟动态获取数据
      }
    },
    created (){
      //模拟从服务器动态异步获取
      setTimeout(()=>{

        this.comments = [
          {
            username:'Tom',
            content:'Vue还不错！',
            id: Date.now()
          },
          {
            username:'JACK',
            content: 'Vue相当给力！',
            id: Date.now()
          }
        ]
      },1000)
    },
    /*
    将commentAdd,commentList 两个组件映射为标签
    */
    components:{
      commentAdd,
      commentList
    },
    methods:{
        addComment (comment){
          this.comments.unshift(comment);
        },
      deleteComment (comment) {
          var index = this.comments.indexOf(comment);
          this.comments.splice(index,1);
      }
    }
  }
</script>
<style>
  img{
    width: 100px;
    height: 100px;
  }
</style>
