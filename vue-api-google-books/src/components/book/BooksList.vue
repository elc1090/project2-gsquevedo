<template>
    <div class="books-list">
        <BookItem v-for="book in books" :key="book.id" :books="book"/>
    </div>
</template>
<script>
import BookItem from './BookItem.vue';

export default {
    name: "BookLists",
    components: {
        BookItem
    },
    setup(){
        return {}
    },
    props: {
        books: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>

</style>