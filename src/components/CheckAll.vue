<template>
  <div>
    <input type="checkBox" :checked="!anyRemaining" @change="checkAllTodos" />
    <span>&nbsp;Check all</span>
  </div>
</template>

<script>
export default {
  name: "CheckAll",
  props: ["anyRemaining"],
  methods: {
    checkAllTodos() {
      this.$emit("check-all");
    }
  }
};
</script>

<style scoped>
</style>