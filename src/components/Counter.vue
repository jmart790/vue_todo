<template>
  <div>
    <div class="count-container">
      <div class="todo-count" :class="remainingColor">{{remaining}}</div>

      <div class="todo- text">left!</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: ["remaining"],
  computed: {
    remainingColor() {
      if (this.remaining === 0) {
        return "none";
      } else if (this.remaining < 5) {
        return "small";
      } else if (this.remaining < 10) {
        return "medium";
      } else {
        return "large";
      }
    }
  }
};
</script>

<style scoped lang="scss">
.count-container {
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  font-size: 2rem;
  font-weight: bold;

  .todo-count {
    width: 3rem;
    height: 3rem;
    display: grid;
    place-items: center;
    border-radius: 50%;
    margin: 0 0.5rem;
    color: rgba(0, 0, 0, 0.79);
  }
  .none {
    background-image: linear-gradient(120deg, #d4fc79 0%, #6fdb7d 100%);
  }
  .small {
    background-image: linear-gradient(to right, #fbf396 0%, #ffcc8d 100%);
  }
  .medium {
    background-image: linear-gradient(to right, #ffac8d 0%, #f7950b 100%);
  }
  .large {
    background-image: linear-gradient(to right, #fca496 0%, #f9748f 100%);
  }
}
</style>