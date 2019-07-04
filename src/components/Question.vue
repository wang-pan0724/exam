<template>
  <div class="question">
    <Radio
      title="1. 中国共产党第十九次全国代表大会，是在全面建成小康社会决胜阶段、中国特色社会主义进入_____的关键时期召开的一次十分重要的大会。"
      v-model="value1"
      :options="options1"
    />
    <p class="selected">您选中的是：{{value1}}</p>

    <CheckList title="普通多选框列表" v-model="value" @getData="getinfo" :options="options" />
    <p class="selected">您选中的是：{{value}}</p>

    <div class="nextBtn" @click="nextQuestion()">下一题</div>
  </div>
</template>

<script>
import Radio from "@/components/radio.vue";
import CheckList from "@/components/checkList.vue";
export default {
  name: "Question",
  components: {
    Radio,
    CheckList
  },
  data() {
    return {
      value: "",
      value1: "",
      options1: [" A. 新时期", " B. 新阶段", "C. 新征程", "D. 新时代"],
      options: ["optionA", "optionB", "optionC"]
    };
  },
  methods: {
    getinfo(arr) {
      this.value = arr;
    },
    nextQuestion(){
        console.log("下一题")
    }
  }
};
</script>
<style>
.selected {
  font-size: 14px;
  padding: 10px;
}

.nextBtn {
  font-size: 0.22rem;
  width: 80%;
  margin: 0.4rem auto 0px;
  background: #ccc;
  line-height: 0.54rem;
  height: 0.54rem;
  border-radius: 3px;
  text-align: center;
}
</style>
