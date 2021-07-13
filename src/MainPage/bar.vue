
<template>
<div style="margin:auto;height: auto;text-align:center; background-image: url(http://pic1.win4000.com/wallpaper/2017-10-12/59df06d7c561f.jpg); background-repeat:repeat;">
    <div class="hidScroller">


  <el-container >
          <el-aside width="300px" style="padding:20px;">
          <el-container class="asid-rank" style="height:350px">
            <el-main >
              <img src="../assets/1.jpg" height="120px" width="120px" style="border-radius:50%"/>
              <p><b>贴吧名字</b></p>
              <el-button type="warning" size="small">关注</el-button>
              <br>

              <el-collapse  @change="handleChange" >
                <el-collapse-item title="贴吧简介" name="1">
                  <div>与现实生活一致：与现实生活的流程、逻辑保持一致，遵循用户习惯的语言和概念；</div>
                  <div>在界面中一致：所有的元素和结构需保持一致，比如：设计样式、图标和文本、元素的位置等。</div>
                </el-collapse-item>
                <el-collapse-item title="基本信息" name="2">
                  <div>控制反馈：通过界面样式和交互动效让用户可以清晰的感知自己的操作；</div>
                  <div>页面反馈：操作后，通过页面元素的变化清晰地展现当前状态。</div>
                </el-collapse-item>
              </el-collapse>


              <el-col :span="10">
                <el-row v-for="(barItem,index) in bar" :key="index">
                  <span>
                    <el-button type="text" @click="toBar(barItem.router)">{{index+1}} {{barItem.BarTitle}}</el-button>
                  </span>
                </el-row>
              </el-col>
            </el-main>
            </el-container>

      </el-aside>

      <el-main  style="border-radius:25px;">
        <div style="padding:20px;border-radius:25px;"  class="back"  >
        <el-row>
          <b>帖子浏览</b>
               <el-row v-for="(barItem,index) in barData" :key="index">
                       <el-divider></el-divider>
                 <el-col :span="4" style="float:left">
                   <p >{{barItem.postTime}} </p>
                
                   </el-col>
                 <el-col :span="4"><p class="postTitle" style="float:left"> {{barItem.postTitle}} </p>
                   </el-col>
                 <el-col :span="4"><p class="postUser" style="float:left"> {{barItem.postUser}} </p></el-col>
                  
                </el-row>
                
        </el-row>
        </div>
        <div>
        <br>
        <el-divider></el-divider>
        </div>
         <el-container  class="back" style="padding:20px;border-radius:25px;" >
           <el-main>
            <b style="float:left">发帖</b>
            <div>
            <el-row>
                <el-input placeholder="请填写标题" v-model="enter" size="media" clearable> </el-input>
            </el-row>
            <br>
            </div>
            <div>
            <el-row>
                <el-input type="textarea" :rows="2" placeholder="请输入内容" v-model="textarea">  </el-input>
            </el-row>
            <el-row>
              <br>
                <el-button type="primary" style="float:left" @click="onSubmit">发表</el-button>
            </el-row>
            </div>
           </el-main>
          </el-container>
      </el-main>
                <el-aside width="200px" style="padding:20px;" >
          <el-container class="asid-rank">
            <el-main>

              <p><b>贴吧排行</b></p>

              <el-col :span="10">
                <el-row v-for="(barItem,index) in bar" :key="index">
                  <span>
                    <el-button type="text" @click="toBar(barItem.router)">{{index+1}} {{barItem.BarTitle}}</el-button>
                  </span>
                </el-row>
              </el-col>
            </el-main>
            </el-container>

      </el-aside>
  </el-container>



    </div>
</div>
</template>

<script>
  export default {
    data() {
      
     
      return {
        barData:[
          {
            postTitle:"hello",
            postTime:"123",
            postUser:"123",
            BarImgUrl:require('../assets/1.jpg')
            

          },
          {
            postTitle:"hello",
            postTime:"123",
            postUser:"123",
            BarImgUrl:require('../assets/1.jpg')

          },
          {
            postTitle:"hello",
            postTime:"123",
            postUser:"123",
            BarImgUrl:require('../assets/1.jpg')

          },
          {
            postTitle:"hello",
            postTime:"123",
            postUser:"123",
            BarImgUrl:require('../assets/2.jpg')

          }
        ],
        
      }
    },
    methods: {
          handleChange(val) {
           console.log(val);
      }
    },

  };
</script>

<style>
.el-header {
    background-color: #B3C0D1;
    color: #333;
    line-height: 60px;
      border-radius: 20px;

    
  }

  .el-aside {
    color: #333;
   
  }
/*最外层透明*/
.el-table, .el-table__expanded-cell{
  background:  #ffffff;

}
/* 表格内背景颜色 */
.el-table th,
.el-table tr,
.el-table td {
      background: hsl(0, 0%, 100%);
}
.mainback{
     background: #40a0ff7c;
        border-color: #40a0ff7c; 
        border-style: solid;  
        border-width: 2px;  
}
.postTitle
{
    font-size:20px;
    cursor:pointer;
    font-weight:bold;
}
.postUser
{
    font-size:5px;
    cursor:pointer;
    font-weight:bold;
}
.bar-header{
   border-color: rgba(255, 255, 255, 0.829);
  background-color: rgba(255, 255, 255, 0.925);
  border-radius: 20px;
    border-style: solid;  
    border-width: 2px;  
  height: 280px;
}
.el-collapse-item__header {
    display: flex;
    align-items: center;
    height: 48px;
    line-height: 48px;
    background-color: rgba(255, 246, 246, 0.034);
    color: #303133;
    cursor: pointer;
    border-bottom: 1px solid #EBEEF5;
    font-size: 13px;
    font-weight: 500;
    transition: border-bottom-color .3s;
    outline: 0;
}
.el-collapse >>> .el-collapse-item{
  background-color: #e9eef3 !important
}
.el-collapse-item >>> .el-collapse-item__header{
  background-color: #e9eef3 !important
}
.el-collapse-item >>> .el-collapse-item__wrap{
  background-color: #e9eef3 !important
}
</style>
