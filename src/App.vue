<template>
  <div id="app">
    <!-- <add-blog></add-blog> -->
    <!-- <show-blogs></show-blogs> -->
    <blog-header></blog-header>
    <router-view></router-view>
  </div>
</template>

<script>
import BlogHeader from './components/BlogHeader'
import AddBlog from './components/AddBlog'
import ShowBlogs from './components/ShowBlogs'

export default {
  name: 'App',
  components: {
    AddBlog,ShowBlogs,BlogHeader
  }
}
</script>
