<template>
  <div class="todo">
    <div>{{ id }} - {{ todo }}</div>
    <button type="button" v-on:click="deleteTodo">Done</button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    id: Number,
    todo: String,
    handleDelete: Function,
  },
  methods: {
    deleteTodo() {
      this.handleDelete(this.id);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todo {
  display: flex;
  padding: 5px;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
  justify-content: space-between;
}
</style>
