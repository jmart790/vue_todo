<template>
  <div id="app">
    <ClearCompleted :todos="todos" v-on:clear-completed="clearCompleted" />
    <FilterTodos :filter="filter" v-on:filter-todos="filterTodos" />
    <CheckAll :anyRemaining="anyRemaining" v-on:check-all="checkAllTodos" />
    <Counter :remaining="remaining" />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos :todosFiltered="todosFiltered" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import ClearCompleted from "../components/ClearCompleted";
import FilterTodos from "../components/FilterTodos";
import CheckAll from "../components/CheckAll";
import Counter from "../components/Counter";
import AddTodo from "../components/AddTodo";
import Todos from "../components/Todos";

export default {
  name: "Home",
  components: {
    ClearCompleted,
    FilterTodos,
    CheckAll,
    Counter,
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: [
        { id: 1, title: "First task", completed: false },
        { id: 2, title: "Second task", completed: true },
        { id: 3, title: "Third task", completed: false }
      ],
      filter: "all"
    };
  },
  computed: {
    remaining() {
      return this.todos.filter(todo => !todo.completed).length;
    },
    anyRemaining() {
      return this.remaining !== 0;
    },
    todosFiltered() {
      if (this.filter == "completed") {
        return this.todos.filter(todo => todo.completed);
      } else if (this.filter == "active") {
        return this.todos.filter(todo => !todo.completed);
      } else {
        return this.todos;
      }
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [newTodo, ...this.todos];
    },
    checkAllTodos() {
      this.todos.forEach(todo => (todo.completed = event.target.checked));
    },
    filterTodos(filter) {
      this.filter = filter;
    },
    clearCompleted() {
      this.todos = this.todos.filter(todo => !todo.completed);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
