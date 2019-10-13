<template>
  <div>
    <div class="todo-count">{{remaining}} left!</div>
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: ["remaining"]
};
</script>

<style scoped>
.todo-count {
  text-align: center;
  font-size: 1rem;
  font-weight: bold;
  padding: 0.5rem;
}
</style>