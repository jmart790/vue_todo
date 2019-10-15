<template>
  <div>
    <div :key="todo.id" v-for="todo in todosFiltered">
      <TodoItem
        :todo="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
        v-on:toggle-complete="$emit('toggle-complete', todo.id)"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todosFiltered"]
};
</script>

<style scoped>
</style>