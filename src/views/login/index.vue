<template>
  <div class="login-container">
    <el-form
      ref="loginForm"
      :model="loginForm"
      :rules="rules"
      class="login-form"
    >
      <div class="title-container">
        <h3 class="title">用户登录</h3>
      </div>
      <el-form-item
        label=""
        prop="userName"
      >
        <i class="el-icon-user" />
        <el-input
          ref="userName"
          v-model="loginForm.userName"
          placeholder="请输入用户名"
        />
      </el-form-item>
      <el-form-item
        ref="userPwd"
        label=""
        prop="userPwd"
      >
        <i class="el-icon-lock" />
        <el-input
          v-model="loginForm.userPwd"
          placeholder="请输入密码"
          type="password"
          maxlength="6"
        />
      </el-form-item>
      <el-form-item label="">
        <el-button
          type="primary"
          class="login_btn"
          @click.native.prevent="handleLogin"
        >登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  name: 'Login',
  data() {
    const validateUserName = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('登录账号为空！'))
      } else {
        callback()
      }
    }
    const validateUserPwd = (rule, value, callback) => {
      if (!value) {
        return callback(new Error('登录密码为空！'))
      } else {
        callback()
      }
    }
    return {
      loginForm: {
        userName: 'admin',
        userPwd: '123456'
      },
      rules: {
        userName: { validator: validateUserName, trigger: 'blur', required: true },
        userPwd: { validator: validateUserPwd, trigger: 'blur', required: true }
      }
    }
  },
  methods: {
    handleLogin() {
      this.$refs.loginForm.validator(valid => {
        alert(valid)
      })
    }
  }
}
</script>
<style lang="scss">
$bg: #283443;
$light_gray: #fff;
$cursor: #fff;
.el-input {
  display: inline-block;
  height: 47px;
  width: 85%;

  input {
    background: transparent;
    border: 0px;
    -webkit-appearance: none;
    border-radius: 0px;
    padding: 12px 5px 12px 15px;
    color: $light_gray;
    height: 47px;
    caret-color: $cursor;

    &:-webkit-autofill {
      box-shadow: 0 0 0px 1000px $bg inset !important;
      -webkit-text-fill-color: $cursor !important;
    }
  }
}
i {
  padding: 6px 5px 6px 15px;
  color: #889aa4;
  vertical-align: middle;
  width: 30px;
  display: inline-block;
  /* height: 10px; */
  /* width: 20px; */
  font-size: 20px;
}
.el-form-item {
  border: 1px solid rgba(255, 255, 255, 0.1);
  background: rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  color: #454545;
}
.login-container {
  min-height: 100%;
  width: 100%;
  background-color: $bg;
  overflow: hidden;
  .login-form {
    position: relative;
    width: 520px;
    max-width: 100%;
    padding: 160px 35px 0;
    margin: 0 auto;
    overflow: hidden;
  }
  .title {
    font-size: 26px;
    color: #eee;
    margin: 0px auto 40px auto;
    text-align: center;
    font-weight: bold;
  }
  .login_btn {
    width: 100%;
  }
}
</style>
