<template>
  <div class="trello-clone">
    <h1>Trello Clone</h1>
    <div class="trello-list" v-for="list in board" v-bind:key="list.listName">
      <div class="trello-list-name">
        {{ list.listName }}
      </div>
      <div
        class="trello-card"
        v-for="(card, index) in list.cards"
        v-bind:key="card"
      >
        <input v-model="list.cards[index]"/>
      </div>
      <div class="trello-add-task" v-on:click="addTask(list.listName)">+</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TrelloClone",
  data() {
    return {
      board: [
        {
          listName: "A",
          cards: ["TaskA", "TaskA2"]
        },
        {
          listName: "B",
          cards: ["TaskB"]
        },
        {
          listName: "C",
          cards: []
        },
        {
          listName: "D",
          cards: ["TaskD"]
        }
      ]
    };
  },
  methods: {
    addTask(listName) {
      const newTask = prompt(listName, "");
      this.board.find(list => list.listName === listName).cards.push(newTask);
    }
  }
};
</script>

<style scoped lang="scss">
@mixin card {
  height: fit-content;
  padding: 10px 0;
  background-color: lightgray;
}

.trello-list {
  display: inline-flex;
  flex-direction: column;
  width: 100px;
  border: 1px solid black;
  margin: 0 20px;

  .trello-list-name {
    @include card;
    background-color: skyblue;
  }

  .trello-card {
    @include card;
    margin: 10px 0 0;
    border: 1px solid black;

    input {
      border: 0;
      width: 100%;
      background-color: transparent;
      text-align: center;
    }

    input:focus {
      outline: 0;
    }
  }

  .trello-add-task {
    @include card;
    margin: 10px 0 0;
    border: 1px solid black;
  }
}
</style>
