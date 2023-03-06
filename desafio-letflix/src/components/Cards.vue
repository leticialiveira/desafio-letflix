<script setup>
defineProps({
    image: String,
    name: String, 
    url: String
})
</script>

<template>
    <article>
        <a :href="url">
            <h1> {{ name }}</h1>
            <img :src="image" alt="filme">
        </a>
    </article>
</template>

<style scoped>
article {
    width: 300px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
    flex-direction: column;
    text-align: center;
}

article a {
    width: 250px;
    font-size: larger;
    font-weight: 200;
    text-decoration: none;
    
}


article h1 {
    width: 250px;
    font-size: larger;
    font-weight: 200;
    color: var(--color-name) ;
    
}


article:hover {
    transform: scale(1.2);
    transition-delay: 0.5s;
}
article h1:hover{
    color: inherit;

}
</style>
