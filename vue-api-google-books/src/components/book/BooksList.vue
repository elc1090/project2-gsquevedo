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
.books-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin: 0 -8px;
    margin-top: 20px;
}

.book-item {
    width: calc(33.333% - 16px);
    margin: 0 8px 16px;
}

.book-info {
    display: block;
    text-align: center;
    text-decoration: none;
}

.book-info img {
    max-width: 100%;
    height: auto;
    margin-bottom: 8px;
}

.book-info h4 {
    margin: 0;
    font-size: 1rem;
    font-weight: 500;
    line-height: 1.2;
}
</style>