<script setup>
defineProps({
    image: String,
    name: String
})
</script>

<template>
    <article>
        <a :url='url'>{{ name }}</a>
        <!-- <h1> {{ name }}</h1> -->
        <img :src="image" alt="filme">
    </article>
</template>

<style scoped>
article {
    width: 350px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
    flex-direction: column;
    
}

article a {
    width: 250px;
    font-family: 'Gloock', serif;
    font-size: larger;
    font-weight: 200;
    text-decoration: none;
}
article img {
    border-radius: 2%;
}

article:hover {
    transform: scale(1.2);
}
</style>
