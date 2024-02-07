<script setup>
import axios from "axios";
import { ref } from "vue";
import { useRoute, useRouter } from "vue-router";

const route = useRoute();
const router = useRouter();
const pokeSprite = ref({});

const back = () => {
    router.push("/pokemons");
};

const getData = async () => {
    console.log(route.params.name);
    try {
        const { data } = await axios.get(
            `https://pokeapi.co/api/v2/pokemon/${route.params.name}`
        );
        pokeSprite.value = data.sprites.front_default;
    } catch (error) {
        console.log(error);
        pokeSprite.value = null;
        
    }
};

getData();
</script>

<template>
<h1>Pokemon: {{ $route.params.name }}</h1>
    <main class="text-center">
        <div v-if="pokeSprite">
            <div class="pokemon-image-container">
            <img class="pokemon-image" :src="pokeSprite" alt="" width="200px" height="200px" />
        
        </div>
        </div>
        <h1 v-else>Pokemon no encontrado...</h1>
        <button @click="back()">Volver al listado</button>
    </main>
</template>


<style>

.pokemon-image-container {
    display: flex;
    justify-content: right; /* Centers the image horizontally */
    align-items: right; /* Centers the image vertically */
  height:   100%; /* Adjust as needed */
}

.pokemon-image {
    max-width:   100%; /* Ensures the image doesn't exceed the container width */
  height: auto; /* Maintains aspect ratio */
}
</style>