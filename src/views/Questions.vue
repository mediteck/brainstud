<template>
  <div class="questions">
    <h1>Brainstud Jeopardy</h1>
    <p>
      In Jeopardy, you get a clue. Based on the clue, you need to think of the
      answer. In this small app, you will make 5 jeopardy questions. At the end,
      you will receive your score.
    </p>
    <Question
      :currentStep="progress + 1"
      :totalSteps="questions.length"
      :question="questions[progress]"
      v-on:next-question="progress++"
      v-if="questions.length > 0"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import Question from "@/components/Question.vue";

export default {
  name: "Home",
  data: function () {
    return {
      questions: [],
      progress: 0,
    };
  },
  components: {
    Question,
  },
  created: function () {
    const url = "https://jservice.io/api/random?count=5";
    this.axios.get(url).then((response) => {
      this.questions = response.data;
    });
  },
};
</script>
