<template>
  <div class="todo-item" :class="{'is-completed': y.completed}">
    <p>
      <input type="checkbox" @change="markComplete" />
      {{y.title}}
      <button class="del" @click="$emit('del-todo', y.id)">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["y"],
  methods: {
    markComplete: function() {
      this.y.completed = !this.y.completed;
    }
  }
};
</script>




<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-completed {
  text-decoration: line-through;
}

.del {
  background: orangered;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>