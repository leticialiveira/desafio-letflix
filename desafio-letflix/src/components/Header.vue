<script setup>
defineProps({
  movie: String
})
defineEmits(['update:movie'])
</script>

<template>
  <header>
    <div class="left">
      <img src="../assets/icons/icon_letflix.png" alt="">
      <a href="./Inicio.vue">Início</a>
      <a href="#series">Séries</a>
      <a href="#filmes">Filmes</a>
      <a href="#bombando">Bombando</a>
      <a href="#lista">Minha lista</a>
      <a href="#idiomas">Navegar por idiomas</a>
    </div>
    <div class="right">
      <input id="movie" type="text"  @input="$emit('update:movie', $event.target.value)" :value="movie" placeholder="Pesquisar filme:" >
      <p>{{ movie }}</p>
    </div>
  </header>
  
</template>

<style>
header {
  background-color: var(--bg-header);
  width: 100vw;
  height: 50px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 800px;
}

header .left {
  display: flex;
  align-items: center;
  gap: 50px;
}

header .left img {
  width: 100px;
}
header .left a {
  text-decoration: none;
  gap: 100px;
}

header .left a:hover {
  color: #FC3535;
}

header .right input {
  border-radius: 5px;
  width: 200px;
  height: 25px;
  padding: 10px 10px 10px 10px;
  color: var(--color-input);
  border: 0;

}
</style>