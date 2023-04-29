<template>
    <div> 
        <h1> {{ volumeInfo.title }}</h1>
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
<styled scoped>
</styled>