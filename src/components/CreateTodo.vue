<template>
  <div class="ui basic content center aligned segment">
    <button
      class="ui basic button icon"
      v-on:click="openForm"
      v-show="!isCreating"
    >
      <i class="plus icon"></i>
    </button>
    <div class="ui centered card" v-show="isCreating">
      <div class="content">
        <div class="ui form">
          <div class="field">
            <label for="title">Title</label>
            <input
              id="title"
              v-model="titleText"
              type="text"
              ref="title"
              defaultValue=""
            />
          </div>
          <div class="field">
            <label for="project">Project</label>
            <input
              id="project"
              type="text"
              v-model="projectText"
              ref="project"
              defaultValue=""
            />
          </div>
          <div class="ui two button attached buttons">
            <button class="ui basic blue button" v-on:click="sendForm()">
              Create
            </button>
            <button class="ui basic red button" v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titleText: '',
      projectText: '',
      isCreating: false,
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (
        this.titleText.trim().length > 0 &&
        this.projectText.trim().length > 0
      ) {
        const { titleText, projectText } = this;
        this.$emit('addTodo', {
          title: titleText,
          project: projectText,
          done: false,
        });
        this.titleText = '';
        this.projectText = '';
      }
      this.isCreating = false;
    },
  },
};
</script>

<style scoped></style>
