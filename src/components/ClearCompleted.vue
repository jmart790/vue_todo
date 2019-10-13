<template>
  <div>
    <button v-if="showClearCompleteBtn" @click="clearCompleted">Clear Completed</button>
  </div>
</template>

<script>
export default {
  name: "ClearCompleted",
  props: ["todos"],
  methods: {
    clearCompleted() {
      this.$emit("clear-completed");
    }
  },
  computed: {
    showClearCompleteBtn() {
      return this.todos.filter(todo => todo.completed).length > 0;
    }
  }
};
</script>

<style scoped>
</style>