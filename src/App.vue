<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "app",
};
</script>

<style>
html {
  overflow-x: hidden;
}
body {
  font-family: "Open Sans", sans-serif;
  margin: 0;
}
#app {
  background: #efefef;
}
.text-center {
  text-align: center;
}
</style>
