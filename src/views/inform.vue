<template>
    <div class="BrowsePost" style="margin:auto;height: 600px;text-align:center; background-image: url(https://static.zhihu.com/heifetz/assets/sign_bg.db29b0fb.png); background-repeat:repeat-y;">
    <div class="back">
  <el-container>
          <el-aside width="300px" style="padding:20px;"></el-aside>
          <el-main>
           
<el-table
    :data="AdList.slice((currentPage-1)*pagesize,currentPage*pagesize)" 
    class="table"
    style="width: 100%">

     <el-table-column
        prop="ADDTIME"
        label="公告发布时间"
        width="250">
      </el-table-column>

     <el-table-column
       prop="ANNOUNCEMENTTITLE"
       label="公告标题"
       alian="center"
       width="350">
      </el-table-column>

      <el-table-column >
        
            <template slot-scope="scope">
              <message :text="scope.row.ANNOUNCEMENTCONTENT"/>
            </template>
        
      </el-table-column>
    

  </el-table>
     
  <el-pagination
  background
  layout="total, prev, pager, next, jumper"
  @size-change="handleSizeChange"
  @current-change="handleCurrentChange"
  :current-page="currentPage"
  
  :page-size="pagesize"
  :total="AdList.length"
>
</el-pagination>
</el-main>
<el-aside width="300px" style="padding:20px;"></el-aside>
  </el-container>
  </div>
</div>
</template>

<script>
import Message from "../Message/message.vue";
  export default {
    data() {
       
      return {
        AdItem:{
            Title:'1111',
            Content:'看到了吗'

        },
        IsVisible:false,
        currentPage:1,
        pagesize:8,
        AdList:[],
      }
    },
    components:{
      Message
    },
    mounted(){
    this.getAd('http://139.196.167.75:5000/api/Announcement');
    },
    created(){
      this.getAd()
    },
     methods: {
        handleSizeChange: function(val) {
            this.pagesize = val;
        },
        handleCurrentChange: function(currentPage) {
            this.currentPage = currentPage;
        },
     
        store:function(item){
        this.AdList=JSON.parse(item);
        console.log(this.AdList);
        },
        async getAd(url){
          
          
          await fetch(url, {
            method: 'GET',
            headers: {
              'Accept': 'application/json',
              'Content-Type': 'application/json'
            },
          })
          .then(response => response.json())
          .then(data => this.store(data));
          console.log("Geted");
        }
    }
  } 
</script>

<style>
.table{
  margin: auto;
}
</style>