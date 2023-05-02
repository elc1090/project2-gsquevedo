<template>
    <div class="query">
        <h1>BUSQUE SEU LIVRO</h1>
        <form @submit.prevent="onSubmit">
            <div>
                <InputText v-model="searchBook" :type="'text'" :placeholder="'Digite as informações do livro'" />
                <ButtonSearch class="btnSearch" :type="'submit'"> Pesquisar </ButtonSearch>
            </div>
            <div class="filter">
                <RadioInput v-model="selected" :name="'radio-group'" :options="group" />
                <SelectOrder name="Filtrar Por: " :options="options"  v-model="orderBy" />
            </div>
            <div v-if="books.length">
                <BooksList :books="books"/>
            </div>
        </form>
    </div>
</template>
  
<script>
import { ref } from "vue";
import axios from "axios";
import InputText from "../InputText.vue";
import ButtonSearch from "../ButtonSearch.vue";
import BooksList from "./BooksList.vue";
import RadioInput from "../RadioInput.vue";
import SelectOrder from '../SelectOrder.vue';

export default {
    name: "SearchBook",
    setup() {
        const books = ref([]);
        const searchBook = ref('');
        const selected = ref('');
        const maxResults = ref('15')
        const orderBy = ref('relevance');

        const group = [
            { label: 'Autor', value: 'author' }, 
            { label: 'Título', value: 'title' }
        ];

        const options = [
            { label: 'Atuais', value: 'newest' },
            { label: 'Relevância', value: 'relevance' }
        ] 

        async function search() {
            try {
                const response = await axios.get(
                    `https://www.googleapis.com/books/v1/volumes?q=${selected.value}:${searchBook.value}&orderBy=${orderBy.value}&maxResults=${maxResults.value}`
                );
                books.value = response.data.items;
            } catch (error) {
                throw new Error("Erro na requisição");
            }
        }

        const onSubmit = () => {
            search();
        };

        return {
            books,
            searchBook,
            selected,
            options,
            group,
            orderBy,
            onSubmit
        };
    },
    components: {
        InputText,
        ButtonSearch,
        BooksList,
        RadioInput,
        SelectOrder
    }
};
</script>
  
<style scoped>
.btnSearch {
    margin-top: 20px;
    width: 120px;
    height: 40px;
    font-size: 1.2rem;
    background-color: #54a89a;
    width: 100%;
    border: none;
    border-radius: 30px;
    color: #fff;
    cursor: pointer;
}
.btnSearch:hover {
    background-color: #459689;
    color: #f3f3f9;
}
.filter{
    display: flex;
    align-content: center;
    justify-content: center;
    gap: 50px;
}
</style>