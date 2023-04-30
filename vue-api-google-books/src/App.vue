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
    margin: 50px;
    text-align: center;
    color: #2c3e50;
}
</style>
