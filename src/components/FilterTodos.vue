<template>
  <div class="filter-btns">
    <button name="all" :class="{active: filter == 'all'}" @click="filterTodos('all')">
      <i v-if="filter == 'all'" class="fas fa-circle"></i>
    </button>
    <label for="all" :class="{bold: filter == 'all'}">All</label>
    <button name="active" :class="{active: filter == 'active'}" @click="filterTodos('active') ">
      <i v-if="filter == 'active'" class="fas fa-circle"></i>
    </button>
    <label for="active" :class="{bold: filter == 'active'}">Active</label>
    <button
      name="completed"
      :class="{active: filter == 'completed'}"
      @click="filterTodos('completed') "
    >
      <i v-if="filter == 'completed'" class="fas fa-circle"></i>
    </button>
    <label for="completed" :class="{bold: filter == 'completed'}">Completed</label>
  </div>
</template>

<script>
export default {
  name: "FilterTodos",
  props: ["filter"],
  methods: {
    filterTodos(filter) {
      this.$emit("filter-todos", filter);
    }
  }
};
</script>

<style scoped lang="scss">
.filter-btns {
  // padding: 5px;
  display: grid;
  align-items: center;
  grid-template-rows: 1fr 1fr 1fr;
  grid-template-columns: auto 1fr;

  button {
    width: 2rem;
    height: 2rem;
    margin: 0.5rem;
    font-size: 0.8rem;
    color: white;
    border: none;
    outline: none;
    border-radius: 50%;
    text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.25);
    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.187);
    background-image: linear-gradient(to top, #dfe9f3 0%, white 100%);
  }

  button:hover {
    cursor: pointer;
  }

  .active {
    background-image: linear-gradient(120deg, #89f7fe 0%, #66a6ff 100%);
  }

  label {
    color: grey;
  }
  label.bold {
    color: black;
  }
}
</style>