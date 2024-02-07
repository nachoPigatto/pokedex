<script setup>
import axios from "axios";
import { ref } from "vue";
import { RouterLink } from "vue-router";

const pokemons = ref([]);

const getData = async () => {
    try {
        const { data } = await axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0.");
        pokemons.value = data.results;
    } catch (error) {
        console.log(error);
    }
};

getData();
</script>


<template>
    <h1></h1>
    <ul>
        <li v-for="(poke, index) in pokemons" :key="index">
      {{ index +  1 }}. <router-link :to="`/pokemons/${poke.name}`">{{ poke.name }}</router-link>
    </li>
    </ul>
</template>

<style>
/* Estilo para la lista de Pokémon */
ul {
    list-style-type: none;
    display: flex; /* Convierte la lista en un contenedor flexbox */
 flex-wrap: wrap; /* Permite que los elementos de la lista se envuelvan en varias líneas */
 justify-content: space-around; /* Distribuye uniformemente los elementos de la lista en la línea con espacios iguales entre ellos */
 margin-left: calc(10px +  10%); /* Moves the list  50px to the right and maintains the original  20% margin */
 text-align: right;
}

/* Estilo para cada elemento de la lista */
li {
 flex: 1 0 20%; /* Permite que los elementos de la lista crezcan y se encogan, pero tienen un límite base de 20% del ancho del contenedor */
 margin: 10px; /* Agrega un margen alrededor de cada elemento de la lista para separarlo de los demás */
}

</style>