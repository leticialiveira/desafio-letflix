<script setup>
import HeaderVue from "./components/Header.vue";
import CardsVue from "./components/Cards.vue";
// Sempre bom lembrar de importar as funções
import { ref, watch, onMounted } from "vue";
import axios from "axios";

const movie = ref("");
const jsonResponse = ref([]);

async function filteredJson() {
  
  // substituindo a variavel pela filtragem
  jsonResponse.value = jsonResponse.value.filter((item) =>
  item.name.toLowerCase().includes(movie.value.toLowerCase())
  )
}

async function getMovies() {
  await axios
  .get("https://api.tvmaze.com/shows")
  /**
   * Depois que for realizado o FETCH na API, o valor retornado está sendo
   * desestruturado e sendo armazenado na variavel 'jsonResponse'
   */
  .then(({ data }) => (jsonResponse.value = data))
  // Caso de um erro, será efetuado um console.error
  .catch(console.error);
}

// Todas vez que a váriavel 'movie' ser alterada, a função 'filteredJson' será executada
watch(movie, filteredJson);

// após a página ser montada, será executada a função 'getMovies'

/**
 * Resolva o problema de pesquisa 
 * Dica:
 * 1. Use uma variavel reativa para pesquisa
 * 2. Use o methodo computed para testa se a variável de pesquisa existe (https://vuejs.org/guide/essentials/computed.html)
 * */ 

onMounted(getMovies);
// computed: {
//   now(() => {
// return
</script>
<template>
  <HeaderVue v-model:movie="movie" />
  <div class="main">
  <h1>Filmes e Séries</h1>
    <div class="grid-cards">
      <CardsVue
      v-for="item in jsonResponse"
        :key="item.id"
        :name="item.name"
        :url="item.url"
        :image="item.image.medium"
      />
    </div>
  </div>
</template>

<style scoped>
.main {
  width: 100vw;
  height: 90vh;
  margin-top: 100px;
}

.main h1 {
  padding-bottom: 40px;
  padding-left: 35px;
}
.grid-cards {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 30px;
}
</style>
