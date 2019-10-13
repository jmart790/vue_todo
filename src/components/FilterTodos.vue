<template>
  <div>
    <button :class="{active: filter == 'all'}" @click="filterTodos('all')">All</button>
    <button :class="{active: filter == 'active'}" @click="filterTodos('active') ">Active</button>
    <button :class="{active: filter == 'completed'}" @click="filterTodos('completed') ">Completed</button>
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

<style scoped>
.active {
  background-color: aqua;
}
</style>