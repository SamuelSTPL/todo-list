<template>
  <li v-bind:class="{ 'is-completed': todo.completed }">
    <input type="checkbox" @change="toggleComplete" />
    <p>{{ todo.title }}</p>
    <button @click="$emit('del-todo', todo.id)" class="del">X</button>
  </li>
</template>
<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object
  },
  methods: {
    toggleComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>
<style scoped>
li {
  position: relative;
  list-style: none;
  display: flex;
  border: 1px solid black;
  min-width: 700px;
  max-width: 700px;
  align-items: center;
  border-radius: 5px;
  padding: 0 20px;
  font-weight: bolder;
  font-size: 1.2rem;
}
li:hover {
  transform: scale(1.05);
  background: rgb(214, 211, 211);
}
.is-completed {
  text-decoration: line-through;
}

input {
  margin-right: 10px;
}
.del {
  background-color: tomato;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  position: absolute;
  right: 5%;
  border: none;
  color: whitesmoke;
}

.del:hover {
  cursor: pointer;
}

.del:focus {
  outline: none;
  border: 1px solid black;
}
</style>
