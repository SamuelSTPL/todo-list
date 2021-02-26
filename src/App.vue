<template>
  <div id="app">
    <Header />
    <router-view />
  </div>
</template>

<script>
import Header from "./components/layouts/Header";
export default {
  name: "app",
  components: {
    Header
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
.btn {
  border: none;
  background: #555;
  color: #fff;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
