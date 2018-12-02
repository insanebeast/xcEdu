
<template>
  <div>
    <el-form :inline="true" :model="params" class="demo-form-inline">
      <el-form-item label="页面名称">
        <el-input v-model="params.pageAliase" placeholder="请输入页面名称"></el-input>
      </el-form-item>
      <el-form-item label="所属站点">
        <el-select v-model="params.siteId" placeholder="请选择所属站点">
          <el-option
            v-for="item in siteList"
            :key="item.siteId"
            :label="item.siteName"
            :value="item.siteId">
          </el-option>
        </el-select>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="query">查询</el-button>
      </el-form-item>
    </el-form>

     <el-table
    :data="list"
    stripe
    style="width: 100%">
        <el-table-column type="index" width="60">
        </el-table-column>
        <el-table-column prop="pageName" label="页面名称" width="120">
        </el-table-column>
        <el-table-column prop="pageAliase" label="别名" width="120">
        </el-table-column>
        <el-table-column prop="pageType" label="页面类型" width="150">
        </el-table-column>
        <el-table-column prop="pageWebPath" label="访问路径" width="250">
        </el-table-column>
        <el-table-column prop="pagePhysicalPath" label="物理路径" width="300">
        </el-table-column>
        <el-table-column prop="pageCreateTime" label="创建时间" width="250" >
        </el-table-column>
      </el-table>
    <el-pagination
      layout="prev, pager, next"
      style="float: right;"
      :total="total"
      :current-page="params.page"
      @current-change="changePage">
    </el-pagination>
  </div>
</template>
<script>
  import * as cmsApi from '../api/cms'

  export default {
    mounted(){
      this.query()
    },
    data() {
      return {
        siteList:[{
          siteId:'5a751fab6abb5044e0d19ea1',
          siteName:'门户主站'
        },{
          siteId:'test',
          siteName:'测试站点'
        }],
        list: [],
        total:50,
        params:{
          page:1,
          size:10,
          pageAliase:'',
          siteId:''
        }
      }
    },
    methods:{
      changePage:function (page) {
        this.params.page = page
        this.query();
      },
      query:function () {
        cmsApi.page_list(this.params.page,this.params.size,this.params).then((res)=>{
          console.log(this.params)
          console.log(res)
          this.total = res.queryResult.total
          this.list = res.queryResult.list
        })
      }
    }
  }


</script>
<style>
  /*编写页面样式，不是必须*/
</style>
