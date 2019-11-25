<template>
  <div>
    <div class="header" @click="back()">
      <span class="left"></span>
       header
    </div>
    <div class="question">
      <Radio
        v-if="data.state == 0"
        :title="data.info.title"
        v-model="value"
        :options="data.info.question"
      />
      <CheckList  v-if="data.state == 1" :title="data.info.title" v-model="value" @getData="getinfo" :options="options"/>

      <p class="selected">您选中的是：{{value}}</p>

      <div class="sure">
        <button @click="submit()">确定</button>
      </div>
      <div v-if="showAnswerArea" class="answerArea">
        <div>正确答案：{{data.info.answer.answerTitle}}</div>
        <div>
          {{data.info.answer.answerDetail}}
        </div>
      </div>
      <div class="nextBtn" @click="nextQuestion()">下一题</div>
    </div>
  </div>
</template>

<script>
import Radio from '@/components/radio.vue'
import CheckList from '@/components/checkList.vue'
export default {
  components: {
    Radio,
    CheckList
  },
  data() {
    return {
      value: '',
      value1: '',
      data: {
        state: '0',
        info: {
          title: '问题阅读和豆瓣都能',
          question: [' A. 新时期', ' B. 新阶段', 'C. 新征程', 'D. 新时代'],
          answer: {
            answerTitle: 'D',
            answerDetail: '解释说明为什么要这么做'
          }
        }
      },
      options: ['optionA', 'optionB', 'optionC'],
      showAnswerArea: false
    }
  },
  methods: {
    getinfo(arr) {
      this.value = arr
    },
    nextQuestion() {
      console.log('下一题')
    },
    back() {
      this.$router.push({path: '/Home'})
    },
    submit() {
      if (this.value !== '') {
        this.showAnswerArea = true
      } else {
        alert('请选择')
      }
    }
  }
}
</script>
<style>
.left {
    position: absolute;
    left: 10px;
    top: 13px;
    width: 10px;
    height: 10px;
    border-top: 2px solid #867f7a;
    border-right: 2px solid #867f7a;
    transform: rotate(-135deg);
    margin-right: -50px;
}
.header{
    font-size: 0.36rem;
    text-align: center;
    height: 0.8rem;
    line-height: 0.8rem;
    background: #000;
    color: #fff;
}
.selected {
  font-size: 14px;
  padding: 10px;
}
.sure{
  text-align: right;
}
.sure button{
  margin-right: 20px;
  padding: 5px 10px;
  background: #26a2ff;
  border-radius: 3px;
  color: #fff;
  outline: none;
}

.nextBtn {
    font-size: 0.22rem;
    width: 100%;
    margin: 0.4rem auto 0px;
    background: #ccc;
    line-height: 0.54rem;
    height: 0.54rem;
    border-radius: 3px;
    text-align: center;
    position: fixed;
    bottom: 0px;
}
.answerArea {
  font-size: 0.32rem;
}
</style>
