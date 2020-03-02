<template>
  <el-form :model="queryForm" ref="queryForm" :inline="true">
    <el-form-item label="班级" label-width="120px">
      <el-select v-model="queryForm.classNo" placeholder="请选择班级">
        <el-option label="拉丁舞一班" value="0"></el-option>
        <el-option label="拉丁舞二班" value="1"></el-option>
      </el-select>
    </el-form-item>
    <el-form-item label="学生姓名" label-width="120px">
      <el-input v-model="queryForm.studentName" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="warning" @click="doReset">重置</el-button>
      <el-button type="primary" @click="doQuery">查询</el-button>
    </el-form-item>
  </el-form>
</template>

<script>
  import list from './data'
    export default {
        name: "QueryForm",
      data(){
        return {
          queryForm:{name:'',idNo: ''}
        }
      },
      methods: {
        doReset(){
          this.$refs['queryForm'].resetFields();
        },
        doQuery(){
          let data = list;
          //TODO
          this.$emit("updateData",data)
        },
      }
    }
</script>

<style scoped>

</style>
