<script>
export default {
  name: 'GameBoard',
  props: {
    msg: String,
    category1: Object,
    category2: Object,
    category3: Object,
    category4: Object,
  },
  data() {
    return {};
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
  <div class="gameBoard" id="gameBoard">
    <table>
      <tr>
        <th>Player 1</th>
        <th>Player 2</th>
        <th>Player 3</th>
        <th></th>
      </tr>
      <tr>
        <th>{{category1}}</th>
        <th></th>
        <th></th>
        <th></th>
      </tr>
      <tr v-for="(data, index) in category1" class="easy">
        <span v-for="category in category1">${{ index + 1 }}00</span>
        <td
          v-if="category1[index].difficulty === 'easy'"
          @click="answerClicked"
        >
          {{ category1[index].answer }}
        </td>
      </tr>
      <tr class="easy">
        <td>$200</td>
        <td>$200</td>
        <td>$200</td>
        <td>$200</td>
      </tr>
      <tr class="medium">
        <td>$300</td>
        <td>$300</td>
        <td>$300</td>
        <td>$300</td>
      </tr>
      <tr class="medium">
        <td>$400</td>
        <td>$400</td>
        <td>$400</td>
        <td>$400</td>
      </tr>
      <tr class="hard">
        <td>$500</td>
        <td>$500</td>
        <td>$500</td>
        <td>$500</td>
      </tr>
    </table>
  </div>
  <div class="gameMessages"></div>
</template>

<style scoped>
table {
  border: 1px solid black;
  width: 400px;
}
tr {
  border: 1px solid black;
  height: 20%;
}
th {
  border: 1px solid black;
  width: 20%;
}
td {
  border: 1px solid black;
  width: 20%;
}
</style>
