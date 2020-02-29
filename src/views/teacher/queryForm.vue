<template>
  <el-form :model="queryForm" ref="queryForm" :inline="true">
    <el-form-item label="姓名" label-width="120px" prop="name">
      <el-input v-model="queryForm.name" autocomplete="off" ></el-input>
    </el-form-item>
    <el-form-item label="身份证号" label-width="120px" prop="idNo">
      <el-input v-model="queryForm.idNo" autocomplete="off"></el-input>
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
