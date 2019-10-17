<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from "./components/Header";
export default {
  name: "app",
  components: { Header }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Raleway:100,400,700&display=swap");
* {
  /* box-sizing: border-box; */
  margin: 0;
  padding: 0;
}
body {
  margin: 3% auto;
  width: 90vw;
  font-family: "Raleway", sans-serif;
}
</style>
