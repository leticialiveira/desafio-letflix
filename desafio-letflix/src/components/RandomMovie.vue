<script setup lang="ts">
defineProps({
    image:String,
    name: String,
    summary: String,
    url: String
})
</script>

<template>
    <img :src="image" alt=" ">
    <div class="test">
      <h1 >{{name}}</h1>
      <p>{{ summary}}</p>
      <div class="buttons">
        <a :href="url">
          <button> Assistir</button>
        </a>
        <button>Mais informações</button>
      </div>
    </div>
      
</template>

<style scoped>


img {
  width: 465px;
  background-color: var(--bg-image);
}

.test{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
} 

h1{
  width: 500px;
  /* background-color: aqua; */
  text-align: center;
}

p {
  /* background-color: blueviolet; */
  width: 500px;

}
.buttons button{
  width: 150px;
  height: 35px;
  border: 0;
  margin: 10px;
  border-radius: 5%;
}
.buttons a button{
  color: var(--color-input);
}
.buttons button{
  background-color:var(--bg-button-app);
  
}
</style>