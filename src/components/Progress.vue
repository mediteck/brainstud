<template>
  <div class="progress">
    <span>{{ currentStep }}/{{ totalSteps }}</span>
  </div>
</template>

<script>
export default {
  name: "Progress",
  props: {
    currentStep: Number,
    totalSteps: Number,
  },
};
</script>

<style scoped lang="scss">
span {
  color: #bebed2;
  margin-bottom: 27px;
}
</style>
