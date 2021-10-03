<template>
  <div id="app">
    <HelloWorld />
    <HomePage />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import HomePage from "./components/HomePage.vue";



export default {
  name: "App",
  components: {
    HelloWorld,
    HomePage,
    
  },
};
</script>

<style scoped lang="scss" src="./components/scss/_variables.scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
