<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos
      v-bind:todos="todos"
      v-on:del-todo="deleteTodo"
      v-on:add-todo="addTodo"
    />
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";

import axios from "axios";

export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then((res) => {
          this.todos = this.todos.filter((todo) => todo.id !== id);
          return res;
        })
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    }
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
.btn {
  border: none;
  background: #555;
  color: #fff;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
