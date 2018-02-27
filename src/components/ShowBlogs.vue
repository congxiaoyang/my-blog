<template>
  <div v-theme:column="'narrow'" id="show-blogs">
        <h1>博客总览</h1>
        <input type="text" v-model="search" placeholder="搜索">
        <div v-for="blog in filteredBlogs" class="single-blog">
            <router-link v-bind:to="'/blog/' + blog.id"><h2 v-rainbow>{{blog.title | to-uppercase}}</h2></router-link>
            <article>{{blog.body | snippet}}</article>
        </div>
  </div>
</template>

<script>
export default {
  name: 'show-blogs',
  data(){
      return{
          blogs:[],
          search:""
      }
  },
  created(){
    //   this.$http.get('http://jsonplaceholder.typicode.com/posts')
        this.$http.get('./../static/posts.json')
          .then(function(data){
            //   console.log(data);
            this.blogs = data.body.slice(0,10);
            console.log(this.blogs);
          })
  },
  computed:{   // 搜索
      filteredBlogs:function(){
          return this.blogs.filter((blog) =>{
              return blog.title.match(this.search);
          })
      }
  },
  filters:{   // 过滤
      toUppercase(value){
          return value.toUpperCase();
      },
      snippet(value){
          return value.slice(0,100) +"...";
      }

  },
  directives:{   // 自定义组件 格式 v-
      'rainbow':{
            bind(el,binding,vnode){
                el.style.color = "#" + Math.random().toString(16).slice(2,8);
            }
      },
      'theme':{
            bind(el,binding,vnode){
                if(binding.value == 'wide'){
                el.style.maxWidth = '1280px';
                }else if(binding.value == 'narrow'){
                el.style.maxWidth ="560px"
                }

                if(binding.arg == 'column'){
                // el.style.background = "#6677cc";
                el.style.padding = "20px";
                }
            }
      }
  }
}
</script>

<style>
    #show-blogs{
        max-width: 800px;
        margin: 0 auto;
    }
    .single-blog{
        padding: 20px;
        margin: 20px 0;
        box-sizing: border-box;
        background: #eee;
        border: 1px dotted #aaa;
    }

    #show-blogs a{
      color: #444;
      text-decoration: none;
    }

    input[type="text"]{
      padding: 8px;
      width: 100%;
      box-sizing: border-box;
    }

</style>
