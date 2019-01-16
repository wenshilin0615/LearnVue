<template>
      <div class="backlogin">
        <div class="login_box">
          <div class="title">后台登录</div>
            <div>
              <input class="myinput" type="text" placeholder="手机号/用户名" v-model="username" />
            </div>
          <div>
            <input @keyup.13="login" class="myinput" type="password" placeholder="口令" v-model="password" />
          </div>
          <div class="login_other">
            <a href="javascript:;">找回密码</a>
            <input type="checkbox" id="remenberme" />
            <label for="remenberme">记住我</label>
          </div>
          <button :disabled="disablebtn" class="login" @click="login">{{loginText}}</button>
        </div>
      </div>
    </template>
    <script>
  import {
    Toast
  } from 'mint-ui';
  export default {
    name: 'backlogin',
    data() {
      return {
        username: "admin",
        password: "123456",
        disablebtn: false,
        loginText: "登录"
      }
    },
    methods: {
      login() {
        var vm = this;
        this.disablebtn = true;
        this.loginText = "登陆中";
        this.$reqs.post('/users/login', {
          username: this.username,
          password: this.password
        }).then(function (res) {
          if (res.data.status === true) {
            vm.$router.replace('/home');
          } else {
            //弹窗
            Toast({
              message: res.data.errMsg,
            });
            vm.disablebtn = false;
            vm.loginText = "登陆";
          }
        }).catch(function (err) {
          vm.disablebtn = false;
          vm.loginText = "登陆";
        })
      }
    }
  }
</script>
<style scope>
    /* //剩下的样式大家自由发挥 */
</style>