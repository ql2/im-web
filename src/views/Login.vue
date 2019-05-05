<template>
  <el-row
    type="flex"
    justify="center"
    align="middle"
  >
    <el-col :span="5">
      <el-form
        ref="form"
        :model="form"
        :rules="rules"
      >
        <el-form-item prop="username">
          <el-input
            prefix-icon="el-icon-user-solid"
            v-model="form.username"
            placeholder="用户名"
            autoComplete="on"
            autofocus=true
            @focus="clearValidate('form')"
          ></el-input>
        </el-form-item>
        <el-form-item prop="password">
          <el-input
            v-model="form.password"
            show-password
            placeholder="密码"
            prefix-icon="el-icon-lock"
            @keyup.enter.native="onSubmit('form')"
          ></el-input>
        </el-form-item>

        <el-form-item>
          <el-button
            type="primary"
            :loading="loadingVisible"
            @click.native.prevent="onSubmit('form')"
            style="width:100%"
          >登录</el-button>
        </el-form-item>

      </el-form>
    </el-col>
  </el-row>
</template>

<script>
export default {
    data() {
      return {loadingVisible: false,
        form: {
          username: '',
          password:''

        },
        rules: {
          username: [
            { required: true, message: '请输入姓名', trigger: 'blur' },
          ],
          password: [
            { required: true, message: '请输入密码', trigger: 'blur' },
          ],

        }
      }
    },
    methods: {
        clearValidate(formName) {
      this.$refs[formName].clearValidate()
    },
      onSubmit(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            alert('submit!');
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      }
    },
    
  }
</script>
