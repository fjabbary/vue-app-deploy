<template>
  <div>
    <div :key="item.id" v-for="item in x">
      <TodoItem :y="item" v-on:del-todo="$emit('del-todo', item.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
  name: "Todos",
  props: ["x"],
  components: {
    TodoItem
  }
};
</script>

<style scoped>
</style>