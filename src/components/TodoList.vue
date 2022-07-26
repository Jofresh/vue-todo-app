<template>
  <div class="main">
    <div class="form">
      <input
        ref="input"
        type="text"
        v-model="input"
        placeholder="Add a new todo..."
      />
      <button type="button" v-on:click="handleSubmit">Add</button>
    </div>
    <div class="todolist">
      <todo-item
        v-for="(todo, index) in todos"
        :id="index"
        :todo="todo"
        :handleDelete="deleteTodo"
      ></todo-item>
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
  name: 'TodoList',
  components: {
    TodoItem,
  },
  data() {
    return {
      todos: [],
      input: '',
    };
  },
  mounted() {
    this.todos = ['first-todo', 'second-todo', 'third-todo'];
    //this.$refs.input.focus();
  },
  methods: {
    handleSubmit() {
      if (this.input === '') return;

      this.addTodo();
      this.input = '';
      this.$refs.input.focus();
    },
    addTodo() {
      this.todos = [this.input, ...this.todos];
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo, i) => i !== id);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.main {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
.todolist {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
</style>
