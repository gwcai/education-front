<template>
  <div class="app-container">
    <query-form @updateData="updateDataList"></query-form>

    <el-table :data="data" style="width: 100%" border>
      <el-table-column prop="id" label="主键" width="180"></el-table-column>
      <el-table-column prop="classNo" label="班级编号" width="180"></el-table-column>
      <el-table-column prop="className" label="班级名称" width="180"></el-table-column>
      <el-table-column prop="studentName" label="姓名" width="180"></el-table-column>
      <el-table-column prop="classDate" label="上课日期" width="180"></el-table-column>
      <el-table-column prop="courseTimes" label="课次" width="180"></el-table-column>
      <el-table-column prop="attendance" label="考勤情况" width="180"></el-table-column>
      <el-table-column prop="signTime" label="签到时间" width="180"></el-table-column>
      <el-table-column prop="createDate" label="创建日期" width="180"></el-table-column>

      <el-table-column
        fixed="right"
        label="操作"
        width="150">
        <template slot-scope="scope">
          <el-button @click="handleClick(scope.row,false)" type="text" size="small">查看</el-button>
          <el-button @click="handleClick(scope.row,true)" type="text" size="small">编辑</el-button>
          <el-button @click="doDelete(scope.row)" type="text" size="small">删除</el-button>
        </template>
      </el-table-column>
    </el-table>

    <edit-dialog v-if="dialogVisible" :render="dialogVisible" :editable="editable" :form="form" @update="updateDialogVisible"></edit-dialog>
  </div>
</template>

<script>
  import EditDialog from "./editDialog";
  import QueryForm from "./queryForm";

  export default {
    name: "Attendance",
    components: {EditDialog, QueryForm },
    data(){
      return {
        data: [],
        form:{
          name:'',
          gander: '',
          idNo: ''
        },
        dialogVisible: false,
        editable: false,
        title: '详情'
      }
    },
    methods: {
      handleClick(row,edit) {
        if(edit){
          this.title = "编辑信息";
          this.editable = true;
        }else{
          this.title = "详细信息"
          this.editable = false;
        }
        this.form = row;
        this.dialogVisible = true;
      },
      doDelete(row){
        //TODO
      },
      updateDialogVisible(val){
        this.dialogVisible = val;
      },
      updateDataList(data){
        this.$data.data = data;
      }
    }
  }
</script>

<style scoped>

</style>
