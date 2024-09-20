<script>
import GameBoard from './components/GameBoard.vue';
import TileButton from './components/TileButton.vue';

export default {
  data() {
    return {
      category1: [],
      category2: [],
      category3: [],
      category4: [],
      trivia_categories: [
        9, 11, 12, 14, 15, 16, 17, 18, 19, 20, 22, 23, 24, 25, 28, 31,
      ],
    };
  },
  components: {
    GameBoard,
    TileButton,
  },
  methods: {
    sleep() {
      setTimeout(() => console.log('loading...'), 6000);
    },
    getQuestions(category, group) {
      let temp = [];
      for (let i = 0; i < 3; i++) {
        let amount = 2;
        let difficulty = 'easy';
        if (i == 1) {
          difficulty = 'medium';
        }
        if (i == 2) {
          amount = 1;
          difficulty = 'hard';
        }
        const url = `https://opentdb.com/api.php?amount=${amount}&category=${category}&difficulty=${difficulty}&type=boolean`;
        console.log(url);
        fetch(url)
          .then((resp) => resp.json())
          .then((data) => {
            temp = data.results.map((question) => ({
              difficulty: question.difficulty,
              category: question.category,
              answer: question.question,
              correct: question.correct_answer,
            }));
            console.log(temp);
            console.log(group);
            group = group.concat(temp);
          })
          .catch((error) => {
            console.log(JSON.stringify(error));
          });

        this.sleep();
      }
    },
  },
  created: function () {
    console.log('loading questions...');
    this.getQuestions(9, this.category1);
    this.sleep();
    this.getQuestions(11, this.category2);
    this.sleep();
    this.getQuestions(12, this.category3);
    this.sleep();
    this.getQuestions(14, this.category4);
    this.sleep();
    console.log('questions loaded!');
  },
  updated: function () {
    console.log(this.this.category1);
  },
};
</script>

<template>
  <div id="app">
    <p v-for="question in category1">
      {{ question.category }}
    </p>
    <TileButton />
  </div>
  <div>
    <GameBoard
      :category1="category1"
      :category2="category2"
      :category3="category3"
      :category4="category4"
    />
  </div>
  <div>
    <button @click="getQuestions(10, this.category1)">click me!</button>
  </div>
</template>

<style scoped></style>
