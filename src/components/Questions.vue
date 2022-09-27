<template>
  <div class="questions-ctr">
    <div class="progress">
      <div
        class="bar"
        :style="{ width: `${(questionsCount / questions.length) * 100}%` }"
      ></div>
      <div class="status">
        {{ questionsCount }} out of {{ questions.length }} questions answered
      </div>
    </div>
    <transition-group name="fade">
      <div
        class="single-question"
        v-for="(question, qIndex) in questions"
        :key="question.q"
        v-show="questionsCount === qIndex"
      >
        <div class="question">
          {{ question.q }}
        </div>
        <div
          class="answers"
          v-for="answer in question.answers"
          :key="answer.text"
        >
          <div class="answer" @click.prevent="answered(answer.is_correct)">
            {{ answer.text }}
          </div>
        </div>
      </div>
    </transition-group>
  </div>
</template>

<script>
export default {
  props: ["questions", "questionsCount"],
  emits: ["answered"],
  methods: {
    answered(is_correct) {
      this.$emit("answered", is_correct);
    },
  },
};
</script>
