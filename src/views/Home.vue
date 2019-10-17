<template>
  <div id="app" class="app-body">
    <ClearCompleted class="clear" :todos="todos" v-on:clear-completed="clearCompleted" />
    <FilterTodos class="filter" :filter="filter" v-on:filter-todos="filterTodos" />
    <CheckAll class="check-all" :anyRemaining="anyRemaining" v-on:check-all="checkAllTodos" />
    <Counter class="counter" :remaining="remaining" />
    <AddTodo class="add-todo" v-on:add-todo="addTodo" />
    <Todos
      class="todo-list"
      :todosFiltered="todosFiltered"
      v-on:del-todo="deleteTodo"
      v-on:toggle-complete="toggleComplete"
    />
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
    toggleComplete(id) {
      this.todos = this.todos.map(todo => {
        return todo.id === id ? { ...todo, completed: !todo.completed } : todo;
      });
    },
    checkAllTodos() {
      if (this.anyRemaining) {
        this.todos.forEach(todo => (todo.completed = true));
      } else {
        this.todos.forEach(todo => (todo.completed = false));
      }
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

<style lang="scss">
.app-body {
  height: 75vh;
  border: 2px solid black;
  border-radius: 0 0 25px 25px;
  box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.287);
  display: grid;
  grid-template-columns: 1fr 1fr 1fr max-content;
  grid-template-rows: max-content 1fr 1fr auto minmax(4rem, max-content);
  grid-template-areas:
    "input input input remaining"
    "todos todos todos remaining"
    "todos todos todos filters"
    "todos todos todos check-all"
    "todos todos todos clear-complete";
  gap: 1rem;
  padding: 1rem;

  .counter {
    grid-area: remaining;
    // border: 2px solid black;
  }
  .add-todo {
    grid-area: input;
    // border: 2px solid black;
  }
  .todo-list {
    grid-area: todos;
    // border: 2px solid black;
    overflow: scroll;
  }
  .filter {
    grid-area: filters;
    // border: 2px solid black;
  }
  .check-all {
    grid-area: check-all;
    // border: 2px solid black;
  }
  .clear {
    grid-area: clear-complete;
    // border: 2px solid black;
  }
}
</style>
