<template>
  <div id="app">
      <router-view></router-view>
  </div>
</template>

<script>

export default {
  name: 'app',

  mounted(){
    // 请求是否登录的接口
    this.$axios({
        url: "/admin/account/islogin",
        withCredentials: true,
      }).then(res => {
      
      //如果是未登录状态，跳转到登录页
      if(res.data.code === "nologin"){
        this.$router.push("/login");
      }
    })
  }
}
</script>

<style>

*{
  margin:0;
  padding:0;
}

.mt20{
  margin-top:20px;
}

.mb20{
  margin-bottom: 20px;
}
</style>
