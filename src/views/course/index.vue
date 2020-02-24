<template>
  <div class="app-container">
    <el-table :data="data" style="width: 100%" border>
      <el-table-column prop="id" label="主键" width="180"></el-table-column>
      <el-table-column prop="no" label="课程编号" width="180"></el-table-column>
      <el-table-column prop="type" label="课程类型" width="180"></el-table-column>
      <el-table-column prop="subtype" label="细类" width="180"></el-table-column>
      <el-table-column prop="classTimes" label="课时" width="180"></el-table-column>
      <el-table-column prop="askForLeave" label="允许请假次数" width="180"></el-table-column>
      <el-table-column prop="status" label="状态" width="180"></el-table-column>
      <el-table-column prop="createdDate" label="创建时间" width="180"></el-table-column>

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
    name: "Course",
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
