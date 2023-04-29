<template>
    <div class="book-item">
        <a :href="volumeInfo.previewLink" class="book-info">
            <template v-if="volumeInfo.imageLinks">
                <img :src="volumeInfo.imageLinks.thumbnail" :alt="volumeInfo.title">
            </template>
            <template v-else>
                <img
                src="https://islandpress.org/sites/default/files/400px%20x%20600px-r01BookNotPictured.jpg"
                :alt="volumeInfo.title"
                width="128"
                >
            </template>
            <h4>{{ volumeInfo.title }}</h4>
        </a>
    </div>
</template>

<script>

export default {
    name: "BookItem",
    components: {
    },
    setup(){
        return {}
    },
    props: {
        books: {
            type: Object,
            required: true
        }
    },
    computed: {
        volumeInfo(){
            return this.books.volumeInfo
        }
    }
}
</script>
