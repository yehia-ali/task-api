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
  background: #efefef;
}
body {
  font-family: "Open Sans", sans-serif;
  margin: 0;
}
.text-center {
  text-align: center;
}
</style>
