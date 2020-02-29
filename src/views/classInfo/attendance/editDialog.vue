<template>
  <el-dialog :title="title" :visible.sync="visible" :before-close="closeDialog" :close-on-click-modal="false">
    <el-form :model="form" ref="form" :rules="rules">
      <el-form-item label="学生姓名" :label-width="formLabelWidth">
        <el-input v-model="form.name" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="班级" :label-width="formLabelWidth">
        <el-select v-model="form.classNo" placeholder="请选择性别">
          <el-option label="拉丁舞一班" value="0"></el-option>
          <el-option label="拉丁舞二班" value="1"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="办卡类型" :label-width="formLabelWidth">
        <el-input v-model="form.cardInfo" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="课时" :label-width="formLabelWidth">
        <el-input v-model="form.classTimes" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="允许请假次数" :label-width="formLabelWidth">
        <el-input v-model="form.askForLeave" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="已请假次数" :label-width="formLabelWidth">
        <el-input v-model="form.leaveTimes" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="入学时间" :label-width="formLabelWidth">
        <el-input v-model="form.enterDate" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="毕业时间" :label-width="formLabelWidth">
        <el-input v-model="form.graduateDate" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="卡状态" :label-width="formLabelWidth">
        <el-input v-model="form.status" autocomplete="off"></el-input>
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
