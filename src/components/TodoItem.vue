<template>
  <div class="todo-item">
    <input type="checkbox" class="complete-btn" v-model="todo.completed" />
    <div :class="{'is-complete':todo.completed}">{{todo.title}}</div>
    <button @click="$emit('del-todo', todo.id)" class="del">x</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
  display: flex;
  justify-content: space-between;
}

.is-complete {
  text-decoration: line-through;
}
.complete-btn {
  border: solid 1px rgba(128, 128, 128, 0.253);
  border-radius: 50%;
  background: white;
  color: #6bb0ff;
  font-size: 1rem;
  cursor: pointer;
  width: 20px;
  height: 20px;
}
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>