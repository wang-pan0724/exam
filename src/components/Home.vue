<template>
  <div>
    <div class="title">KevinYang题库</div>
    <div class="hello" @click="test()">开始测试 ></div>
  </div>
</template>

<script>
import { debug } from "util";
export default {
  name: "Home",
  data() {
    return {
      msg: ""
    };
  },
  created() {
    debugger;
    var token = localStorage.getItem("token");
    if (token == null) {
      this.$router.push({ path: "/Login" });
    }
  },
  methods: {
    test() {
      this.$router.push({ path: "/Question" });
    }
  }
};
</script>
<style>
.title {
  font-size: 28px;
  padding: 30px;
  text-align: center;
}

.hello{
        font-size: 0.3rem;
        text-align: center;
}
</style>
