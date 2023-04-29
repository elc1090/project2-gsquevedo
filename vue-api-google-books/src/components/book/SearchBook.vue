<template>
<div class="query">
    <form @submit.prevent="onSubmit">
    <div>
        <input type="text" v-model="searchTitle" placeholder="Search..." class="input" required>
        <button type="submit" class="button">Search</button>
    </div>
    </form>
</div>
</template>

<script>
import { ref } from "vue";
import axios from "axios";

export default {
    name: "SearchBook",
    props: {
        value: {
        type: String,
        required: true
        }
    },
    setup(props, { emit }) {
        const books = ref([]);
        const searchTitle = ref(props.value);

        async function search() {
            try {
                const response = await axios.get(`https://www.googleapis.com/books/v1/volumes?q=intitle:${searchTitle.value}`);
                books.value = response.data.items;
                console.log(books.value)
            } catch (error) {
                throw new Error('Erro na requisição');
            }
        }

        const onSubmit = () => {
            emit("update:value", searchTitle.value);
            search();
        };

        return {
            books,
            searchTitle,
            onSubmit
        };
    }
};
</script>
  
<style scoped>
</style>
  