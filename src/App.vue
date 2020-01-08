<template>
  <div id="app">
    <TodoList :todos="todos" />
    <AddTodoInput v-on:create-todo="addTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import AddTodoInput from './components/AddTodoInput.vue'

export default {
  name: 'app',
  components: {
    TodoList,
    AddTodoInput
  },
  data() {
    return {
      todos: [
        {
          taskText: "Todo A",
          completed: false
        },
        {
          taskText: "Todo B",
          completed: false
        },
        {
          taskText: "Todo C",
          completed: false
        },
        {
          taskText: "Todo D",
          completed: false
        }
      ]
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
