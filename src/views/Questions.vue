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
    while (this.questions.length < 5) {
      this.questions = [
        ...this.questions,
        {
          id: 138714,
          answer: "the Mississippi",
          question:
            "For some 2,300 miles, this \"Ol' Man River\" just keeps rollin' along " +
            this.questions.length,
          value: 200,
          airdate: "2011-09-20T12:00:00.000Z",
          created_at: "2015-01-22T02:25:40.235Z",
          updated_at: "2015-01-22T02:25:40.235Z",
          category_id: 13530,
          game_id: 3715,
          invalid_count: null,
          category: {
            id: 13530,
            title: "stately rivers",
            created_at: "2014-02-14T02:07:28.163Z",
            updated_at: "2014-02-14T02:07:28.163Z",
            clues_count: 15,
          },
        },
      ];
      console.log();
    }
  },
};
</script>
