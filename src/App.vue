<template>
  <div id="app">
    <AppHeader />
    <Tester />
  </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import Tester from "./components/Tester.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    Tester,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
