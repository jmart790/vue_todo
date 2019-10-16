<template>
  <div class="todo-item">
    <button
      class="toggle-check"
      :class=" todo.completed ? 'checked' : 'unchecked' "
      @click="$emit('toggle-complete', todo.id)"
    >
      <i class="fas fa-check"></i>
    </button>
    <div class="todo-title" :class="{'is-complete':todo.completed}">{{todo.title}}</div>
    <button @click="$emit('del-todo', todo.id)" class="del">
      <i class="fas fa-minus"></i>
    </button>
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

<style lang="scss">
.todo-item {
  display: grid;
  grid-template-columns: auto 1fr auto;
  margin: 10px 5px;
  border-radius: 25px;
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.187);

  .toggle-check,
  .del {
    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.187);
    outline: none;
    border: none;
    border-radius: 50%;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    width: 1.75rem;
    height: 1.75rem;
    transition: 0.3s;
  }

  .toggle-check,
  .toggle-check:hover {
    background-image: linear-gradient(120deg, #d4fc79 0%, #6fdb7d 100%);
  }
  .toggle-check:hover {
    opacity: 1;
    box-shadow: 2px 2px 4px rgba(85, 237, 65, 0.187);
  }
  .checked {
    color: rgba(255, 255, 255, 0.95);
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.084);
  }
  .unchecked,
  .del {
    color: rgba(255, 255, 255, 0.5);
    background-image: linear-gradient(120deg, #e3e3e2 0%, #dadcda 100%);
  }

  .todo-title {
    margin-left: 1rem;
    display: flex;
    align-items: center;
    cursor: default;
  }

  .is-complete {
    font-weight: 100;
    opacity: 0.5;
  }
  .del {
    // background-image: linear-gradient(to left, #f43737 0%, #ff9c7e 100%);
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.084);
  }
  .del:hover {
    // color: rgba(255, 255, 255, 0.95);
    // background-image: linear-gradient(to left, #f43737 0%, #ff9c7e 100%);
    box-shadow: 2px 2px 4px rgba(255, 0, 0, 0.187);
  }
}
.todo-item:hover {
  .del {
    color: rgba(255, 255, 255, 0.95);
    background-image: linear-gradient(to left, #f43737 0%, #ff9c7e 100%);
  }
}
</style>