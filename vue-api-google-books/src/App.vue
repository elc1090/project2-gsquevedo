<template>
  <div id="app">
    <SearchBook/>
  </div>
</template>

<script>

import SearchBook from './components/book/SearchBook.vue';

export default {
  name: 'App',
  components: {
    SearchBook
  }
}
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
