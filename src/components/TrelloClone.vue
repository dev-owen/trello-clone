<template>
  <div class="trello-clone">
    <h1>Trello Clone</h1>
    <div
      class="trello-board"
      v-for="board in data"
      v-bind:key="board.boardName"
    >
      <div class="trello-board-name">{{ board.boardName }}</div>
      <div class="trello-list" v-for="task in board.list" v-bind:key="task">
        {{ task }}
      </div>
      <div class="trello-add-task" v-on:click="addTask(board.boardName)">+</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TrelloClone",
  data() {
    return {
      data: [
        {
          boardName: "A",
          list: ["TaskA", "TaskA2"]
        },
        {
          boardName: "B",
          list: ["TaskB"]
        },
        {
          boardName: "C",
          list: []
        },
        {
          boardName: "D",
          list: ["TaskD"]
        }
      ]
    };
  },
  methods: {
    addTask(boardName) {
      const newTask = prompt(boardName, "");
      this.data.find(b => b.boardName === boardName).list.push(newTask);
    }
  }
};
</script>

<style scoped lang="scss">
@mixin list-item {
  height: fit-content;
  padding: 10px 0;
  background-color: lightgray;
}

.trello-board {
  display: inline-flex;
  flex-direction: column;
  width: 100px;
  border: 1px solid black;
  margin: 0 20px;

  .trello-board-name {
    @include list-item;
    background-color: skyblue;
  }

  .trello-list {
    @include list-item;
    margin: 10px 0 0;
    border: 1px solid black;
  }

  .trello-add-task {
    @include list-item;
    margin: 10px 0 0;
    border: 1px solid black;
  }
}
</style>
