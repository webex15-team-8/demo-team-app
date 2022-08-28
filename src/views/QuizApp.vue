<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2>Q. {{ "パンダの睡眠時間は？" }}</h2>
    <img
      class="quiz-image"
      src="https://via.placeholder.com/300x300"
      url="https://data.arachina.com/information-view/information/word_img/55f0616104c19c775b0d96f10ddc1d30.jpg"
      alt="クイズタイトル"
    />
    <div class="container" id="Quiz">
      <button
        v-for="(choice, i) in quiz.choices"
        v-bind:key="i"
        v-on:click="choiced(choice)"
      >
        {{ choice.text }}
      </button>
    </div>
    <div>{{ answer }}</div>
  </div>
</template>

<script>
export default {}
// eslint-disable-next-line no-undef
const Quiz = {
  data() {
    return {
      answer: "",
      quiz: {
        text: "パンダの睡眠時間は？",
        choices: [
          { text: "2時間", feedback: "2時間寝るのはキリンだよ" },
          { text: "10時間", feedback: "正解！たくさん寝るんです。" },
          { text: "22時間", feedback: "22時間寝るのはコアラだよ" },
        ],
      },
    }
  },
  methods: {
    choiced(choice) {
      this.answer = choice.feedback
    },
  },
}
// eslint-disable-next-line no-undef
Vue.createApp(Quiz).mount("#app")
</script>

<style>
.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.quiz-image {
  height: 300px;
  width: 300px;
  object-fit: contain;
}

.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>
