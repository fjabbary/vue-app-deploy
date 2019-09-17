<template>
  <div>
    <h1>Add New Todo</h1>
    <form @submit="addNewTodo">
      <input type="text" name="title" v-model="title" placeholder="Add new todo.." />
      <input type="submit" value="submit" />
    </form>
  </div>
</template>

<script>
import uuid from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },

  methods: {
    addNewTodo: function(e) {
      e.preventDefault();
      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      };

      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>



<style scoped>
form {
  display: flex;
  margin-bottom: 10px;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>