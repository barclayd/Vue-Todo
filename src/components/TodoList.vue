<template>
  <div>
    <p>
      Completed Tasks: {{ todos.filter(todo => todo.done === true).length }}
    </p>
    <p>Pending Tasks: {{ todos.filter(todo => todo.done === false).length }}</p>
    <Todo
      v-on:completeTodo="completeTodo"
      v-on:deleteTodo="deleteTodo"
      v-for="(todo, index) in todos"
      v-bind:todo="todo"
      :key="index"
    ></Todo>
  </div>
</template>

<script type="text/javascript">
import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    },
    completeTodo(todo) {
      const prevState = this.todos[this.todos.indexOf(todo)].done;
      this.todos[this.todos.indexOf(todo)].done = !prevState;
    },
  },
};
</script>

<style scoped></style>
