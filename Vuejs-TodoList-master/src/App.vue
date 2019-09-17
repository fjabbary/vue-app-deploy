<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="add" />
    <Todos :x="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/layout/Header";
import AddTodo from "./components/AddTodo";
import axios from "axios";

export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => {
        return todo.id !== id;
      });
    },
    add(a) {
      axios
        .post("https://jsonplaceholder.typicode.com/todos")
        .then(res => (this.todos = [...this.todos, a]));
    }
  },

  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => {
        this.todos = res.data;
      });
  }
};
</script>

<style>
#app {
  width: 500px;
  margin: 0 auto;
}
</style>
