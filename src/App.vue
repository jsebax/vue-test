<template>
  <div id="app">
    <Hauls />
  </div>
</template>

<script>
import Hauls from "@/components/Hauls";

export default {
  name: "App",
  components: {
    Hauls
  }
};
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
