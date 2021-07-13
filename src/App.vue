<template>

  <div id="app">
    <el-row v-if="!$route.meta.ifShow">
    <div style="text-align:center;border-bottom:#99a9bf solid 400; height:61px; background-color:white;">
    <el-row >
      <el-row :gutter="20">
        <el-col :span="5">
          <div class="grid-content bg-purple">
            <a style="" href="/#/">
              <img class="logo" height="61px" width="170px" src="https://wx1.sinaimg.cn/orj360/4f5151f6gy1gsdcsyhuj6j21ez0ron0r.jpg">
            </a>
          </div>
        </el-col>
        <el-col :span="11">
          <div class="grid-content bg-purple">
            <input type="text" class="serch_input" id="serch_input" style="padding:0 10px;font-size:1px;width:70%;height:70%;margin-right:10px;border-radius:5px;border:rgb(190, 185, 185) 200 solid;" placeholder="搜索贴吧/贴子/用户">                              
            <el-button type="primary" icon="el-icon-search" @click="search()" style="height:80%;border-radius:5px;font-size:15px;">搜索</el-button>

          </div>
        </el-col>
        <el-col :span="8">
          <div class="grid-content bg-purple" style="text-align:center;">
            <el-menu :router="true" style="width:100%;float:right;text-align:center; border-radius:4px;" class="el-menu-demo" mode="horizontal">
              <el-menu-item index="inform" style="width:30%;">公告</el-menu-item>
              <el-submenu index="2" style="width:30%;" v-if = "UserState">
                <template slot="title">消息</template>
                <el-menu-item index="/CommentPage">评论</el-menu-item>
                <el-menu-item index="/ReplyPage">回复</el-menu-item>
                <el-menu-item index="/priMessage">私信</el-menu-item>
              </el-submenu>
              <el-menu-item v-if = "!UserState"  index="/Login">登录/注册</el-menu-item>
              <el-submenu index="4" v-if = "UserState" style="width:40%;"> 
                <template slot="title">个人中心</template>
                <el-menu-item index="/activity">个人主页</el-menu-item>
                <el-menu-item index="Logout" @click="Logout()">注销</el-menu-item>
              </el-submenu>
            </el-menu>
          </div>
        </el-col>
      </el-row>
    </el-row>
  </div>
    </el-row>
      <router-view />
  </div>
  
</template>
<script>
export default {
  mounted()
  {
    this.setUserState();
  },
  methods:{
     search:function() {
        this.$router.replace({path: '/Search'});
      },
    setUserState()
    {
      var state = localStorage.getItem("state");
      this.UserState = state;
    },
    Logout()
    {
      localStorage.clear();
      this.$router.replace({path: '/redirct'});
      location.reload();
    },
    toLogin()
    {
      this.$router.push({name:'Login'});
    }
  },
  data(){
    return{
      UserState:false,
    }
  }
}
</script>
<style>
@import url("//unpkg.com/element-ui@2.15.3/lib/theme-chalk/index.css");
  .main_body {
    margin-top: 61px;
    width: 80%;
    height: 800px;
    background-color: rgba(255, 255, 255, 0.8);
  }

  .comment {
    border-radius: 10px;
    width: 98%;
    background-color: #fff;
    height: 350px;
    margin: 0 auto;
    margin-bottom: 60px;
  }

  .side-block {
    border-radius: 10px;
    margin-bottom: 20px;
  }

  .input{
    border:rgb(190, 185, 185) 200 solid;
    box-shadow: 0ch;
  }

  .el-row {
    margin-bottom: 0px;
    height: 60px;
  }
  .el-col {
    border-radius: 4px;
    height: 60px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: white;
  }
  .bg-purple-light {
    background: #e5e9f2;
    height:60px;
    margin: 0;
  }
  .grid-content {
    border-radius: 4px;
    height:60px;
    line-height:60px;
    font-weight: 600;
    font-size: 15px;
    box-shadow: 0 2px 3px rgb(18 18 18 / 10%);
    margin: 0px auto;
  }
  .row-bg {
    padding: 2px 0;
    background-color: #f9fafc;
  }

  .nav {
    box-shadow: 0 3px 3px rgb(18 18 18 / 10%);
    border-bottom: #99a9bf solid 400;
    height: 60px;
  }

  * {
    margin: 0;
    padding: 0;
  }

  .item {
  margin-top: 2px;
  margin-left: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin: 0;
  text-align: center;
  color: #2c3e50;
  width: 1440px;
  height: 850px;
  background-image: url(https://static.zhihu.com/heifetz/assets/sign_bg.db29b0fb.png);
  background-repeat: repeat-y;
}

#nav {
  padding: 45px;
  padding-bottom: 25px ;
}

#nav a {
  font-weight: bold;
  line-height: 35px;
  text-decoration: none;
  color: #2c3e50;
}
#nav a:hover{
  color: #318de2;
}

#nav a.router-link-exact-active {
  color: #2581d6;
  border-bottom:#2581d6 solid;
}

body {
  background-image: url(/assets/loginbg.png);
}

</style>
