<template>
  <el-dialog :title="title" :visible.sync="visible" :before-close="closeDialog" :close-on-click-modal="false">
    <el-form :model="form" ref="form" :rules="rules">
      <el-form-item label="班级" :label-width="formLabelWidth">
        <el-select v-model="form.classNo" placeholder="请选择班级">
          <el-option label="拉丁舞一班" value="0"></el-option>
          <el-option label="拉丁舞二班" value="1"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="上课日期" :label-width="formLabelWidth">
        <el-date-picker
          v-model="form.classDate" type="date" placeholder="选择上课日期">
        </el-date-picker>
      </el-form-item>
      <el-form-item label="开始时间" :label-width="formLabelWidth">
        <el-time-select
          v-model="form.startTime"
          :picker-options="{
            selectableRange: '8:30:00 - 20:30:00'
          }"
          placeholder="选择时间">
        </el-time-select>
      </el-form-item>
      <el-form-item label="结束时间" :label-width="formLabelWidth">
        <el-time-select
          v-model="form.endTime"
          :picker-options="{
            selectableRange: '8:30:00 - 23:30:00'
          }"
          placeholder="选择时间">
        </el-time-select>
      </el-form-item>
      <el-form-item label="课次" :label-width="formLabelWidth">
        <el-input v-model="form.courseTimes" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="上课老师" :label-width="formLabelWidth">
        <el-select v-model="form.teacherId" placeholder="请选择老师">
          <el-option label="王老师" value="0"></el-option>
          <el-option label="李老师" value="1"></el-option>
        </el-select>
      </el-form-item>
    </el-form>
    <div slot="footer" class="dialog-footer" v-if="editable">
      <el-button @click="doCancel">取 消</el-button>
      <el-button type="primary" @click="submitForm">确 定</el-button>
    </div>
  </el-dialog>
</template>

<script>
    export default {
        name: "EditDialog",
        props: {
          title: String,
          form: Object,
          render:{
            type: Boolean,
            default: false
          },
          editable: {
            type: Boolean,
            default: false
          }
        },
        data() {
          return {
            visible: this.render,
            formLabelWidth:'120px',
            rules:{
              name: [
                { required: true, message: '请输入名称', trigger: 'blur' }
              ]
            }
          }
        },
      methods:{
        submitForm() {
          this.$refs['form'].validate((valid) => {
            if (valid) {
              alert('submit!')
            } else {
              console.log('error submit!!')
              return false
            }
          })
        },
        doCancel(){
          this.visible = false;
          this.$emit('update', this.visible)
        },
        resetForm() {
          this.$refs['form'].resetFields()
        },
        closeDialog(done) {
          console.log(this.visible);
          this.$refs['form'].clearValidate()
          done()
          this.$emit('update', this.visible)
        }
      }
    }
</script>

<style scoped>

</style>
