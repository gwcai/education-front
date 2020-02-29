<template>
  <el-dialog :title="title" :visible.sync="visible" :before-close="closeDialog" :close-on-click-modal="false">
    <el-form :model="form" ref="form" :rules="rules">
      <el-form-item label="课程编号" :label-width="formLabelWidth">
        <el-input v-model="form.no" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="课程类型" :label-width="formLabelWidth">
        <el-input v-model="form.type" placeholder=""></el-input>
      </el-form-item>
      <el-form-item label="课程细类" :label-width="formLabelWidth">
        <el-input v-model="form.subtype" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="总课时" :label-width="formLabelWidth">
        <el-input v-model="form.classTimes" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="允许请假次数" :label-width="formLabelWidth">
        <el-input v-model="form.askForLeave" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="课程状态" :label-width="formLabelWidth">
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
              no: [
                { required: true, message: '请输入课程编号', trigger: 'blur' }
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
