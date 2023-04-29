<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <ListsBooks/>
  </div>
</template>

<script>

import ListsBooks from './components/book/ListsBooks.vue';

export default {
  name: 'App',
  components: {
    ListsBooks
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
