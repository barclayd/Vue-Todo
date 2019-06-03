<template>
  <div class="ui centered card">
    <div class="content" v-show="!isEditing">
      <div class="header">{{ todo.title }}</div>
      <div class="meta">
        {{ todo.project }}
      </div>
      <div class="extra content">
        <span class="right floated edit icon" v-on:click="showForm">
          <i class="edit icon"></i>
        </span>
      </div>
    </div>
    <span class="right floated trash icon" v-on:click="deleteTodo(todo)">
      <i class="trash icon"></i>
    </span>
    <!-- Form appears visible when isEditing is true-->
    <div class="content" v-show="isEditing">
      <div class="ui form">
        <div class="field">
          <label for="title">Title</label>
          <input id="title" type="text" v-model="todo.title" />
        </div>
        <div class="field">
          <label for="project">Project</label>
          <input id="project" type="text" v-model="todo.project" />
        </div>
        <div class="ui two button attached buttons">
          <button class="ui basic blue button" v-on:click="hideForm">
            Close ❌
          </button>
        </div>
      </div>
    </div>
    <div
      class="ui bottom attached green basic button"
      v-show="!isEditing && todo.done"
      :disabled="isEditing"
      v-on:click="completeTodo(todo)"
    >
      Completed
    </div>
    <div
      class="ui bottom attached red basic button"
      v-show="!isEditing && !todo.done"
      v-on:click="completeTodo(todo)"
    >
      Pending
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteTodo(todo) {
      this.$emit('deleteTodo', todo);
    },
    completeTodo(todo) {
      this.$emit('completeTodo', todo);
    },
  },
};
</script>

<style scoped></style>
