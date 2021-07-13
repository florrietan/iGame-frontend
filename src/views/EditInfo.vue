<template>

<el-row>

    <br>
    <el-row :gutter="6">
  <el-col :span="10" :offset="2"><div class="grid-content" style="background-color:transparent;">
      <el-form ref="form" :model="UserInfo" label-width="80px" >
    <el-form-item label="用户昵称" style="background-color:transparent;">
        <el-input v-model= "UserInfo.NICKNAME" ></el-input>
    </el-form-item>

    <el-form-item label="性别">
      <el-select v-model = "UserInfo.GENDER" style="float:left;">
         <el-option label="男" :value= 1 ></el-option>
         <el-option label="女" :value= 0 ></el-option>
      </el-select>
    </el-form-item>

  <el-form-item label="出生日期">
    <el-col :span="11">
      <el-date-picker type="date" placeholder="选择日期" v-model="UserInfo.date1" style="width: 100%;"></el-date-picker>
    </el-col>
  </el-form-item>

    <el-form-item label="居住地">
     <el-input v-model = "UserInfo.LOCATION"></el-input>
    </el-form-item>

  <el-form-item label = "我的电话">
    <el-input v-model = "UserInfo.TELEPHONE"></el-input>
  </el-form-item>

  <el-form-item label="简介">
    <el-input type="textarea" v-model = "UserInfo.SIGNATURE"></el-input>
  </el-form-item>

  <el-form-item>
    <el-button type="primary" @click="onSubmit">保存</el-button>
    <el-button>取消</el-button>
  </el-form-item>
</el-form>
</div></el-col>
  
</el-row>
</el-row>

</template>



<script>
import axios from 'axios'
//import func from 'vue-editor-bridge';
 export default {
   mounted(){
     this.setUserID();
     this.getInfo(this.UserID);
     
   },
    data() {
      return {
        form: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
        UserID:"",
        UserInfo:{},
      }
    },
    methods: {
      onSubmit:function() {
        this.getInfo();
        axios.get("url")
        .then()
        console.log('submit!');

      },
      setUserID()
    {
      var storeID = localStorage.getItem("userID");
      this.UserID = storeID;
    },
    store(res)
    {
      
      console.log(res);
      this.UserInfo=JSON.parse(res)[0];
      
      console.log(JSON.parse(res));
    },
    async getInfo(params) {
      var url='http://139.196.167.75:5000/api/SignIn'+'/'+params;
      console.log(url);
      await fetch(url, {
          method: 'GET',
          headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
          },
          //body: JSON.stringify(formData)
        })
          .then(res => res.json())
          .then(res => this.store(res))
          .catch(error => console.log('error is', error));}
    },
      returnUser:function()
      { 
          this.$router.replace({path: '/UserPage'})
      }
    }
  
</script>