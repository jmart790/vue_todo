<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" placeholder="Add Todo..." />
      <button type="submit" value="Submit" class="btn">
        <i class="fas fa-plus" />
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const todo = this.title.trim();
      if (todo.length > 0) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        };
        this.$emit("add-todo", newTodo);
      } else {
        alert("Sorry you cannot enter empty to-dos");
      }
      this.title = "";
    }
  }
};
</script>

<style scoped lang="scss">
form {
  display: grid;
  grid-template-columns: 1fr auto;
  border-radius: 25px;
  box-shadow: 4px 4px 12px rgba(0, 0, 0, 0.287);

  input[type="text"] {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    outline: none;
    font-size: 1.25rem;
    padding: 5px 15px;
    border: none;
    border-radius: 25px;
  }
  button[type="submit"] {
    background-image: linear-gradient(120deg, #89f7fe 0%, #66a6ff 100%);
    color: #ffffff;
    border: none;
    border-radius: 50%;
    height: 2.5rem;
    width: 2.5rem;
    font-size: 1.25rem;
    transition: 0.3s;
    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.187);
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.084);
    outline: none;

    :hover,
    :focus {
      cursor: pointer;
      box-shadow: 2px 2px 4px rgba(46, 156, 225, 0.187);
    }
  }
}
</style>
