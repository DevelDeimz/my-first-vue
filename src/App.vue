<template>
  <div id="app">
    <PostList/>
  </div>
</template>

<script>
import PostList from "./components/PostList.vue";

export default {
  components: {
    PostList
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
