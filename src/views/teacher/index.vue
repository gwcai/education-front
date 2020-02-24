<template>
  <div class="app-container">
    <el-table :data="data" style="width: 100%" border>
      <el-table-column prop="id" label="主键" width="180"></el-table-column>
      <el-table-column prop="no" label="编号" width="180"></el-table-column>
      <el-table-column prop="name" label="姓名" width="180"></el-table-column>
      <el-table-column prop="gander" label="性别" width="180"></el-table-column>
      <el-table-column prop="idNo" label="身份证号" width="180"></el-table-column>
      <el-table-column prop="phoneNo" label="电话号码" width="180"></el-table-column>
      <el-table-column prop="major" label="专业" width="180"></el-table-column>
      <el-table-column prop="status" label="状态" width="180"></el-table-column>
      <el-table-column prop="createDate" label="创建时间" width="180"></el-table-column>

      <el-table-column
        label="操作"
        width="100">
        <template slot-scope="scope">
          <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
          <el-button type="text" size="small">编辑</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  import list from './data'
  export default {
    name: "Teacher",
    data(){
      return {
        data: list,
      }
    },
    methods: {
      handleClick(row) {
        console.log(row);
      }
    }
  }
</script>

<style scoped>

</style>
