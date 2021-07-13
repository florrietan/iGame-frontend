<template>

<div>
   
<div>
<el-container  style="height: 500px; border: 1px solid #eee">
<el-aside width="300px" class="asid" style="border-radius:10px;background-color:rgba(255, 255, 255, 0.8);margin-top:7px;padding:2px;">
  <br>
    <img src="https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fup.enterdesk.com%2Fedpic%2Fc8%2Fdd%2Fb9%2Fc8ddb934a69d90216f1b406cf3975475.jpg&refer=http%3A%2F%2Fup.enterdesk.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=jpeg?sec=1628668047&t=1ffbd058e5f38c29f8a9757421ff7503" height="180px" width="180px" style="border-radius:50%"/>
    <br><br>
    <p><b> {{UserName}} </b></p>
    <br><br>
    <el-menu   :router="true" :default-active="$path='/UserPage'" :collapse-transition="true">
      <el-menu-item index="UserPage" >我的主页</el-menu-item>
      <el-menu-item index="EditInfo">修改个人资料</el-menu-item>
      </el-menu>
</el-aside>
<el-main style="border-radius:10px;background-color:rgba(255, 255, 255, 0.8);margin-left:13px;margin-top:7px;">

  <div style="border-radius:10px;background-color:rgba(255, 255, 255, 0.8);margin-left:13px;margin-top:7px;">
    <button></button>
      <transition name="slide-fade">
      <!--路由占位符-->
      <router-view></router-view>
      </transition>
  </div>
</el-main>
</el-container>
  </div>
</div>
</template>

<script>
// @ is an alias to /src
export default {
  mounted(){
   this.setUserName();
  },
    methods: {
    EditInfo:function()
    {
      this.$router.replace({path: '/EditInfo'})
    },
     setUserName()
    {
      var storeID = localStorage.getItem("userID");
      this.UserName = storeID;
    }
    },
    
  data()
  {
    return{
      UserName:"我是楼主哈哈哈"
    }
  }
}
</script>

<style>

.el-header{
  background-color: #a7cdff;
    color: #333;
    text-align: center;
    line-height: 60px;
}

/* 可以设置不同的进入和离开动画 */
/* 设置持续时间和动画函数 */
.slide-fade-enter-active {
  transition: all .4s ease;
}
.slide-fade-leave-active {
  transition: all 0s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
.background{
    width:100%;  
    height:100%;  /**宽高100%是为了图片铺满屏幕 */
    z-index:-1;
    position: absolute;
}
 
.front{
    z-index:1;
    position: absolute;
}
.asid{
  box-shadow: 1px 1px 9px #e4e4e4
}
</style>

