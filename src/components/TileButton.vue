<script>
export default {
  name: 'TileButton',
  props: {
    Question: Object,
    correct: Boolean,
  },
  data() {
    return {
      msg: 'hello ',
    };
  },
  methods: {
    answerClicked() {
      alert('hello world!');
    },
  },
  mounted() {},
};
</script>

<template>
  <button v-if="Question" :class="correct" @click="answerClicked">
    {{ question.value }}
  </button>
</template>

<style scoped>
button {
  background-color: blue;
  border-radius: 10px;
  color: yellow;
  font-weight: bold;
  padding: 20px;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;

  &.inactive {
    background-color: red;
  }

  &.correct {
    background-color: green;
  }

  &:not(.inactive) {
    cursor: pointer;

    &:hover {
      background-color: purple;
    }
  }
}
</style>
