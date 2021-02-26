<template>
  <div class="wrapper">
    <ul v-for="todo in todos" :key="todo.id">
      <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" />
    </ul>
  </div>
</template>
<script>
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  props: {
    todos: Array
  },
  components: {
    TodoItem
  }
};
</script>
<style>
.wrapper {
  margin-top: 50px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
ul {
  margin: 5px 0 0 0;
  padding-inline-start: 0;
}
</style>
