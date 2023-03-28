<script setup lang="ts">
defineProps({
    image:String,
    original:String,
    name: String,
    summary: String,
    url: String
})
</script>

<template>
    <div class="test">
      <h1 >{{name}}</h1>
      <p>{{ summary}}</p>
      <div class="buttons">
        <a :href="url">
          <button> Assistir</button>
        </a>
        <button >Mais informações</button>
      </div>
      <!-- <div class="testando">
        <button></button>
        <button></button>
        <button></button>
        <button></button>
        <button></button>
      </div> -->
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
  background-color: var(--color-all);
}

.buttons a button:hover{
  background-color: var(--bg-button-app);
}
.buttons button{
  background-color:var(--bg-button-app);
  
}

/* .testando {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

.testando button{
  border-radius: 50%;
  background-color: whitesmoke;
  width: 15px;
  height: 15px;
  border: 0;
} */

</style>