<template>
  <div id="app">
    <TodoList v-bind:todos="todos"></TodoList>
    <CreateTodo v-on:addTodo="addTodo"></CreateTodo>
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [
        {
          title: 'Todo A',
          project: 'Project A',
          done: false,
        },
        {
          title: 'Todo B',
          project: 'Project B',
          done: true,
        },
        {
          title: 'Todo C',
          project: 'Project C',
          done: true,
        },
        {
          title: 'Todo D',
          project: 'Project D',
          done: true,
        },
      ],
    };
  },
  methods: {
    addTodo(todo) {
      this.todos.push(todo);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
