<template>
  <div class="checkall-container">
    <button :class="{checked: !anyRemaining}" @click="checkAllTodos">
      <i class="fas fa-check"></i>
    </button>
    <label for="checkall-btn">{{labelText}}</label>
  </div>
</template>

<script>
export default {
  name: "CheckAll",
  props: ["anyRemaining"],
  computed: {
    labelText() {
      return this.anyRemaining ? "Check All" : "Uncheck All";
    }
  },
  methods: {
    checkAllTodos() {
      this.$emit("check-all");
    }
  }
};
</script>

<style scoped lang="scss">
.checkall-container {
  // padding: 10px;
  display: grid;
  align-items: center;
  grid-template-columns: auto 1fr;
  border-radius: 15px;
  box-shadow: 4px 4px 12px rgba(0, 0, 0, 0.287);

  button {
    background-image: linear-gradient(120deg, #d4fc79 0%, #6fdb7d 100%);
    outline: none;
    border: none;
    border-radius: 50%;
    margin: 0.5rem;
    font-size: 1rem;
    cursor: pointer;
    width: 2rem;
    height: 2rem;
    box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.187);
    color: rgba(255, 255, 255, 0.4);
    transition: 0.3s;
  }
  button:hover {
    box-shadow: 2px 2px 4px rgba(85, 237, 65, 0.187);
  }

  .checked {
    color: rgba(255, 255, 255, 1);
  }
}
</style>