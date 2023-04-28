<template>
    <ImageBook/>
</template>
<script>
import { ref } from 'vue'
import ImageBook from './ImageBook.vue'

export default {
    name: "ListsBooks",
    props: {

    },
    components: {
        ImageBook
    },
    setup(){
        return {}
    },
}
</script>

<style scoped>

</style>