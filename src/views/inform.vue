
<template>
    <div class="BrowsePost" style="margin:auto;height: 800px;text-align:center; background-image: url(https://static.zhihu.com/heifetz/assets/sign_bg.db29b0fb.png); background-repeat:repeat-y;">
    <div class="back">
  <el-container>
          <el-aside width="300px" style="padding:20px;"></el-aside>
          <el-main>
<el-table
    :data="tableData.slice((currentPage-1)*pagesize,currentPage*pagesize)" 
    stripe
    fit
    style="width:100%;">
     <el-table-column
        prop="date"
        width="180">
      </el-table-column>

     <el-table-column
       prop="address"
       label="重要通知！！！！！！！！！！！！"
       width="300">
      </el-table-column>


      <el-table-column 
        prop="name"
        
        >
        <div style="padding: 17px;">
         <el-button type="text" class="button" @click="ShowDialog(AdItem)">{{topic}}</el-button>
         <el-dialog :title="AdItem.Title" :visible.sync="IsVisible">
            {{AdItem.Content}}
        </el-dialog>

       </div>      
      </el-table-column>
      
      
    
     
  </el-table>
  <el-pagination
  background
  layout="total, prev, pager, next, jumper"
  @size-change="handleSizeChange"
  @current-change="handleCurrentChange"
  :current-page="currentPage"
  
  :page-size="pagesize"
  :total="tableData.length"
>
</el-pagination>
</el-main>
<el-aside width="300px" style="padding:20px;"></el-aside>
  </el-container>
</div>
</div>
</template>

<script>
  export default {
    data() {
       
      return {
        tableData: [{
          date: '2016-05-02',
          name: '1',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '2',
          address: '上海市普陀区金沙江路 1517 弄'
        }, {
          date: '2016-05-01',
          name: '3',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '4',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '5',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '6',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '7',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '8',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '9',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '10',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '11',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '12',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '13',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '14',
          address: '上海市普陀区金沙江路 1516 弄'
        }, {
          date: '2016-05-03',
          name: '15',
          address: '上海市普陀区金沙江路 1516 弄'
        },
        {
          date: '2016-05-03',
          name: '116',
          address: '上海市普陀区金沙江路 1516 弄'
        }],
        AdItem:{
            Title:'1111',
            Content:'看到了吗'

        },
        IsVisible:false,
        currentPage:1,
        pagesize:5,
        number:'通知！！！！！！！！！！！！',
        topic:'点我点我点我！！',
        name: '我是发帖人',
      }
    },
     methods: {
        handleSizeChange: function(val) {
            this.pagesize = val;
        },
        handleCurrentChange: function(currentPage) {
            this.currentPage = currentPage;
        },
        ShowDialog:function(AdItem){
            this.IsVisible=true;
            this.Content=AdItem.Content;
        }
    }

  }
</script>

<style>
.back{
   background: rgba(255,255,255,.7);  
        border-color: rgba(255,255,255,.8);  
        border-style: solid;  
        border-width: 2px;  
}
</style>
