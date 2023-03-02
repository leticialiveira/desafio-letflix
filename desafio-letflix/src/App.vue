<script setup>
import HeaderVue from './components/Header.vue';
import CardsVue from './components/Cards.vue';
// import jsonTest from './mock/test.json'
import {ref} from "vue"
import axios from "axios"

const movie = ref('')
const jsonResponse = ref(null)
const resultJson = ref([])


function searchAxio() {
axios.get("https://api.tvmaze.com/shows")
    .then((response) => {
      updateFilteredAxios(response.data)
    })
}

function updateFilteredAxios(result) {
  result.filter(item => item)
}

searchAxio()

</script>

<template>
  <HeaderVue v-model:movie="movie"/>
  <div class="main">
    <h1> Filmes e Séries:</h1>
    <div class="grid-cards">
      <!-- Você esta pegando o resultado de filteredJson, e nele não tem nenhum tratamento, você precisa retornar o valor da sua função -->
      <!-- O seu key, você está passando o item completo, em vez do item.title -->
      <!-- O key continua errado -->
      <!-- os ID não se repetem e são os mais seguros para colocar dentro do key -->
      <CardsVue v-for="item in searchAxio()" :key="item.id" :name="item.name" :image="item.image.original" />
      <!-- todos os cards sumiirammm aaa -->
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
  grid-template-columns: repeat(5,1fr);
  gap: 40px;
}

</style>
