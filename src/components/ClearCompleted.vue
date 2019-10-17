<template>
  <div class="clear-completed-container" v-if="showClearCompleteBtn">
    <button name="clearCompleted" @click="clearCompleted">
      <i class="fas fa-minus"></i>
    </button>
    <label for="clearCompleted">Clear Completed</label>
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

<style scoped lang="scss">
.clear-completed-container {
  display: grid;
  align-items: center;
  grid-template-columns: auto 1fr;
  border-radius: 15px;
  box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.287);

  button {
    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.187);
    outline: none;
    border: none;
    border-radius: 50%;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    width: 2rem;
    height: 2rem;
    margin: 0.5rem;
    background-image: linear-gradient(to left, #f43737 0%, #ff9c7e 100%);
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.084);
    transition: 0.3s;
  }

  button:hover {
    box-shadow: 2px 2px 4px rgba(255, 0, 0, 0.187);
  }
}
</style>