<template>
  <div>
    <el-button type="primary" size="small" @click="query">查询</el-button>
    <el-table
      :data="list"
      stripe
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
    </el-table>
    <el-pagination
      layout="prev, pager, next"
      style="float: right;"
      :total="total"
      @current-change="changePage">
    </el-pagination>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        list: [{
          date: '2016-05-02',
          name: '邹文景',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄'
        }],
        total:50
      }
    },
    methods:{
      changePage:function () {
        this.query();
      },
      query:function () {
        alert("查询");
      }
    }
  }


</script>
<style>
  /*编写页面样式，不是必须*/
</style>
