<template>
  <div class="question">
    <div class="center">
      <Progress :currentStep="currentStep" :totalSteps="totalSteps" />

      <p class="bold">{{ question.question }}</p>
    </div>

    <label for="answer" class="bold">What is your answer?</label>
    <input
      required
      v-model="answer"
      type="text"
      name="answer"
      ref="answer"
      id="answer"
    />

    <div class="result">
      <div class="correct" v-show="answered && correct">is correct</div>
      <div class="incorrect" v-show="answered && !correct">
        is incorrect. The answer was {{ question.answer }}
      </div>
      <div v-show="currentStep == totalSteps && answered" class="score">
        Your final score is: {{ score }}
      </div>
    </div>

    <div class="actions">
      <button
        v-show="!answered"
        class="button button-primary"
        id="give-answer"
        @click="checkAnswer()"
        :disabled="!isAnswered ? true : false"
      >
        Give answer
      </button>
      <button
        v-show="answered && currentStep < totalSteps"
        class="button button-primary"
        id="next-question"
        @click="nextQuestion()"
      >
        Next question
      </button>
    </div>
  </div>
</template>

<script>
import Progress from "@/components/Progress.vue";

export default {
  name: "Question",
  data: function () {
    return {
      answered: false,
      correct: false,
      answer: "",
      score: 0,
    };
  },
  components: {
    Progress,
  },
  props: {
    question: Object,
    currentStep: Number,
    totalSteps: Number,
  },
  mounted: function () {
    console.log(this.question.answer);
  },
  watch: {
    question: function (newVal) {
      console.log(newVal.answer);
    },
  },
  methods: {
    checkAnswer: function () {
      this.correct = this.answer === this.question.answer;
      this.answered = true;
      if (this.correct) this.score++;
    },
    nextQuestion: function () {
      this.answered = false;
      this.correct = false;
      this.answer = "";

      this.$emit("next-question");
    },
  },
  computed: {
    isAnswered: function () {
      return this.answer !== "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.question {
  background: #fafaff;
  border: 1px solid #1e1e32;
  padding: 24px 45px;

  background: #fafaff;
  border: 1px solid #1e1e32;
  box-sizing: border-box;
  border-radius: 30px;
  .center {
    text-align: center;
  }
}

.bold {
  font-family: EinaBold;
}

label {
  text-align: left;
  padding: 0 16px;
  display: block;
}

.actions {
  overflow: hidden;

  #give-answer,
  #next-question {
    float: left;
  }
  #next-question {
    float: right;
  }
}

.result {
  font-family: EinaBold;
  font-size: 18px;
  line-height: 24.89px;
  line-height: 24.89px;
  min-height: 24.89px;
  padding: 10px 16px;

  .correct {
    color: #3ec100;
  }
  .incorrect {
    color: #c10000;
  }
}
</style>
