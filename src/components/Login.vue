<template>
  <div class="hello">
    <div class="title">KevinYang题库</div>
    <div class="userinfo">
      <label for="name">用户名：</label>
      <input type="text" v-model="name" />
    </div>
    <div class="userinfo">
      <label for="password">密码：</label>
      <input type="password" v-model="password" />
    </div>
    <div class="loginBtn" @click="login">登录</div>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      name: "",
      password: ""
    };
  },
  created() {},
  methods: {
    login() {
      console.log(this.name);
      console.log(this.password);
      if (this.name.length > 0 && this.password.length > 0) {
        localStorage.setItem("token", new Date());
        this.$router.push({ path: "/Home" });
      }
    }
  }
};
</script>
<style>
.title {
  font-size: 28px;
  padding: 30px;
  text-align: center;
  margin-bottom: 70px;
}

.userinfo {
  height: 34px;
  display: flex;
  width: 80%;
  margin: 10px auto;
}

.userinfo label {
  width: 80px;
  display: block;
  line-height: 34px;
  font-size: 0.2rem;
}

.userinfo input {
  flex: 1;
  border: 0px;
  padding: 0px 10px;
  outline: 0px;
}

.loginBtn {
  width: 80%;
  margin: 30px auto;
  background: #ccc;
  height: 36px;
  line-height: 36px;
  border-radius: 3px;
      font-size: 0.21rem;
}
</style>