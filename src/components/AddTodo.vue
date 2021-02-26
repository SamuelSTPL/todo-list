<template>
  <form class="form" @submit="addTodo">
    <input type="text" v-model="title" placeholder="Add Todo..." />
    <input type="submit" value="Add" class="btn" />
  </form>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      // Prevent the auto refresh
      e.preventDefault();
      // Only fire if there is content
      if (this.title.length === 0) return;
      //   Create a new Todo Object
      const newTodo = {
        title: this.title,
        completed: false
      };

      //   Send up to parent
      this.$emit("add-todo", newTodo);
      //   Reset content
      this.title = "";
    }
  }
};
</script>

<style scoped>
.form {
  display: flex;
  width: 700px;
  margin: 50px auto;
  height: 50px;
  font-size: 1.3rem;
}
input[type="text"] {
  padding: 5px;
  flex: 10;
}

input[type="submit"] {
  flex: 2;
}
input[type="submit"]:hover {
  cursor: pointer;
}
</style>
