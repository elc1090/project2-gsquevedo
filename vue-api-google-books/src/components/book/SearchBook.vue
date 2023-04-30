<template>
    <div class="query">
      <h1>Google Books API</h1>
      <form @submit.prevent="onSubmit">
        <div>
          <InputText v-model="searchTitle" :type="'text'" :placeholder="'Digite o titulo do livro'" />
          <ButtonSearch class="btnSearch" :type="'submit'"> Pesquisar </ButtonSearch>
        </div>
        <div class="radio">
            <RadioInput v-model="selected" :name="'search'" :options="[{ label: 'Autor', value: 'author' }, { label: 'Título', value: 'title' }]" />
        </div>
        <div v-if="books.length">
          <BooksList :books="books" />
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
  
    export default {
      name: "SearchBook",
      setup() {
        const books = ref([]);
        const searchTitle = ref("");
        const selected = ref("");
  
        async function search() {
          try {
            console.log(selected.value, searchTitle.value)
            const response = await axios.get(
              `https://www.googleapis.com/books/v1/volumes?q=${selected.value}:${searchTitle.value}&orderBy=relevance`
            );
            books.value = response.data.items;
            console.log(books.value);
          } catch (error) {
            throw new Error("Erro na requisição");
          }
        }
  
        const onSubmit = () => {
          search();
        };
  
        return {
          books,
          searchTitle,
          onSubmit,
          selected,
        };
      },
      components: {
        InputText,
        ButtonSearch,
        BooksList,
        RadioInput,
      },
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
</style>
  