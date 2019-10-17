<template>
  <div class="todos-container">
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

<style scoped lang="scss">
.todos-container {
  border-radius: 15px;
  box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.287);
  overflow: scroll;
  overflow-x: hidden;
}
::-webkit-scrollbar {
  width: 0px;
  height: 0px;
}
</style>