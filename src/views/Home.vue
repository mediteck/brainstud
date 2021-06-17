<template>
  <div class="home">
    <h1>Brainstud Jeopardy</h1>
    <p>
      In Jeopardy, you get a clue. Based on the clue, you need to think of the
      answer. In this small app, you will make 5 jeopardy questions. At the end,
      you will receive your score.
    </p>

    <router-link to="/questions" class="button button-primary"
      >Start!</router-link
    >
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
};
</script>
