<template id="">
  <nav>
    <ul>
      <li>
        <router-link to="/" exact>博客</router-link>
        <router-link to='/add' exact>添加博客</router-link>
      </li>
    </ul>
  </nav>
</template>

<script type="text/javascript">

</script>

<style scoped>
  nav{
    background: crimson;
    padding: 30px 0;
    margin-bottom: 40px;
  }
  ul{
    list-style-type: none;
    text-align: center;
    margin: 0;
  }
  li{
    display: inline-block;
    margin: 0 10px;
  }
  a{
    color: #fff;
    text-decoration: none;
    border-radius: 5px;
    padding: 12px;
  }

  .router-link-active{
    background: rgba(255,255,255,0.8);
    color: #444;
  }

</style>
