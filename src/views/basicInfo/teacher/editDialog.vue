<template>
  <el-dialog :title="title" :visible.sync="visible" :before-close="closeDialog" :close-on-click-modal="false">
    <el-form :model="form" ref="form" :rules="rules">
      <el-form-item label="姓名" :label-width="formLabelWidth">
        <el-input v-model="form.name" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="性别" :label-width="formLabelWidth">
        <el-select v-model="form.gander" placeholder="请选择性别">
          <el-option label="男" value="0"></el-option>
          <el-option label="女" value="1"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="身份证号" :label-width="formLabelWidth">
        <el-input v-model="form.idNo" autocomplete="off"></el-input>
      </el-form-item>
      <el-form-item label="联系电话" :label-width="formLabelWidth">
        <el-input v-model="form.phoneNo" autocomplete="off"></el-input>
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
                { required: true, message: '请输入姓名', trigger: 'blur' }
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
          this.$refs['form'].clearValidate()
          done()
          this.$emit('update', this.visible)
        }
      }
    }
</script>

<style scoped>

</style>
