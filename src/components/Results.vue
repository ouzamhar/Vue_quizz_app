<template>
  <div class="result">
    <div class="title">{{ results[resultIndex].title }}</div>
    <div class="desc">{{ results[resultIndex].desc }}</div>
  </div>
</template>

<script>
export default {
  props: ["correctAnswers", "results"],
  computed: {
    resultIndex() {
      let index = 0;
      this.results.forEach((result, idx) => {
        if (
          this.correctAnswers >= result.min &&
          this.correctAnswers <= result.max
        ) {
          index = idx;
        }
      });
      return index;
    },
  },
};
</script>
