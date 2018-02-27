<template id="">
  <div class="" id="single-blog">
    <h1>{{blog.title}}</h1>
    <article class="">
      {{blog.body}}
    </article>
  </div>
</template>
<script type="text/javascript">
  export default{
    name:"single-blog",
    data(){
      return{
        id:this.$route.params.id,
        blog:{}  // 展示当前id的博客
      }
    },
    created(){
      this.$http.get('http://jsonplaceholder.typicode.com/posts/' + this.id)
          .then(function(data){
            console.log(data);
            this.blog = data.body
          })
    }
  }
</script>
<style scoped>
  #single-blog{
    max-width: 960px;
    margin: 0 auto;
    padding: 20px;
    background: #eee;
    border: 1px dotted #aaa;
  }
</style>
