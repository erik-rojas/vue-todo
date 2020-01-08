<template>
  <div class="todo-item">
    <div class="task-text">{{ todo.taskText }}</div>
    <div class="btn-list">
      <button class="btn btn-complete" v-if="!todo.completed" v-on:click="completeTodo(todo)">O</button>
      <button class="btn btn-delete" v-on:click="deleteTodo(todo)">X</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  methods: {
    completeTodo(todo) {
      this.$emit("complete-todo", todo)
    },
    deleteTodo(todo) {
      this.$emit("delete-todo", todo)
    }
  }
};
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #d3d3d3;
  border-radius: 6px;
  padding: 15px 20px;
}
.task-text {
  font-size: 20px;
}
.btn-list {
  display: flex;
}
.btn {
  font-size: 20px;
  padding: 5px 9px;
  border-radius: 5px;
  margin: 0 3px;
  color: white;
  outline: none;
}
.btn-complete {
  background-color: green;
}
.btn-delete {
  background-color: red;
}
</style>
