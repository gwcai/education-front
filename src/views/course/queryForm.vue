<template>
  <el-form :model="queryForm" ref="queryForm" :inline="true">
    <el-form-item label="课程编号" label-width="120px" prop="name">
      <el-input v-model="queryForm.no" autocomplete="off" ></el-input>
    </el-form-item>
    <el-form-item label="课程类型" label-width="120px" prop="idNo">
      <el-input v-model="queryForm.type" autocomplete="off"></el-input>
    </el-form-item>
    <el-form-item label="课程细类" label-width="120px" prop="idNo">
      <el-input v-model="queryForm.subtype" autocomplete="off"></el-input>
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
