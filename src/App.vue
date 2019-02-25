<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <Traning/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Traning from "./components/Traning";

export default {
  name: "App",
  components: {
    HelloWorld,
    Traning
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
