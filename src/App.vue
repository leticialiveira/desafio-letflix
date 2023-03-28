<script setup>
import HeaderVue from "./components/Header.vue";
import CardsVue from "./components/Cards.vue";
import RandomMovieVue from "./components/RandomMovie.vue"
import { ref, watch, onMounted } from "vue";
import axios from "axios";

const movie = ref("");
const jsonResponse = ref([]);
const search = ref(jsonResponse | '')
const randomMovie = ref([])

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
  await randoMovil()
  await filteredJson()
}
// computed: { 
  async function filteredJson() {  
    // substituindo a variavel pela filtragem
    search.value = jsonResponse.value.filter((item) => item.name.toLowerCase().includes(movie.value.toLowerCase()))
  }
  //   filteredJson(() => {
    //     return (filteredJson)
    
    //   })
    // }  
    // Todas vez que a váriavel 'movie' ser alterada, a função 'filteredJson' será executada
    watch(movie, filteredJson);
    
    async function randoMovil() {
       return  randomMovie.value = jsonResponse.value[Math.floor(Math.random() * jsonResponse.value.length)] 
    }

    // !tentativa de filtro pra pegar a linguagem de cada 
    // async function movieLanguages (){
    //   return search.value = jsonResponse.language.value.filter((item) => item.language)
    // }

// após a página ser montada, será executada a função 'getMovies'
onMounted(getMovies);
</script>
<template>
  <HeaderVue v-model:movie="movie" />
  <div class="main">
    <div class="chosen-movie">
      <RandomMovieVue 
      :key="randomMovie.id"
      :image="randomMovie.original"
      :name="randomMovie.name"
      :summary="randomMovie.summary" 
      :url="randomMovie.url" 
      /> 
      </div>
      <h1>Continuar assistindo como </h1>
      <div class="grid-cards">
        <CardsVue
        v-for="item in search"
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
}

.main h1 {
  padding-bottom: 70px;
  padding-left: 35px;
  font-size: larger;
}

.main .chosen-movie{
  background-color:var(--bg-chosen-movie);
  height: 700px;
  width: 100vw;
  display: flex;
  justify-content: center;
  gap: 30px;
}

.grid-cards {
  display: grid;
  grid-template-columns: repeat(7, 235px);
  gap: 30px;
}
</style>
