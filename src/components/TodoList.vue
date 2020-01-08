<template>
  <div class="todo-list">
    <div class="title">To do:</div>
    <TodoItem
      v-for="(todo, index) in inCompletedTodo"
      v-bind:key="index"
      v-on:delete-todo="onDelete"
      v-on:complete-todo="onComplete"
      v-bind:todo="todo"
    />
    <div class="separate-line" v-if="completedTodo.length > 0"></div>
    <TodoItem
      v-for="(todo, index) in completedTodo"
      v-bind:key="index+'completed'"
      v-on:delete-todo="onDelete"
      v-on:complete-todo="onComplete"
      v-bind:todo="todo"
    />
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  props: ["todos"],
  components: {
    TodoItem
  },
  methods: {
    onDelete(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    onComplete(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].completed = true;
    }
  },
  computed: {
    completedTodo () {
      return this.todos.filter(item => item.completed);
    },
    inCompletedTodo () {
      return this.todos.filter(item => !item.completed);
    }
  }
};
</script>

<style scoped>
.todo-list {
  display: flex;
  flex-direction: column;
  width: 30%;
  border: 1px solid #d3d3d3;
  border-radius: 6px;
  padding: 20px;
  margin-bottom: 30px;
}
.title {
  font-size: 30px;
  font-weight: bold;
  align-self: flex-start;
  padding-bottom: 15px;
}
.separate-line {
  width: 100%;
  height: 1px;
  background-color: #d3d3d3;
  margin: 20px 0;
}
</style>