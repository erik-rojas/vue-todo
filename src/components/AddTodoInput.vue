<template>
  <div class="create-todo">
    <div class="input-section">
      <div class="label">Task</div>
      <input v-model="taskText" type="text" ref="task" placeholder="What do you need to do?">
    </div>
    <button class="btn-save" v-on:click="createTodo">
      Save Item
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      taskText: ""
    };
  },
  methods: {
    createTodo() {
      if (this.taskText.length > 0) {
        this.$emit("create-todo", {
          taskText: this.taskText,
          completed: false
        });
      }
    }
  }
};
</script>

<style scoped>
.create-todo {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 30%;
}
.input-section {
  display: flex;
  width: calc(100% - 30px);
  align-items: center;
  padding: 20px 0 20px 30px;
}
.label {
  font-size: 20px;
  font-weight: bold;
  width: 80px;
  text-align: left;
}
input {
  font-size: 20px;
  padding: 8px 15px;
  border-radius: 6px;
  border: 1px solid #d3d3d3;
  width: calc(100% - 80px);
}
.btn-save {
  font-size: 20px;
  color: white;
  background-color: blue;
  padding: 8px 15px;
  border-radius: 8px;
  align-self: flex-end;
}
</style>