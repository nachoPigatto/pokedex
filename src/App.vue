<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { useRoute } from 'vue-router';

const route = useRoute();

</script>
<template>
  <header class="header" v-if="!isPokemonListPage">
     <img alt="Vue logo" class="logo" src="@/assets/descarga.jpg" />
 
     <div class="navigation">
       <RouterLink to="/" class="nav-link">Home</RouterLink>
       <RouterLink to="/pokemons" class="nav-link">Pokemons</RouterLink>
     </div>
  </header>
 
  <RouterView />
 </template>
  

  <script>
  export default {
    computed: {
      isPokemonListPage() {
        return this.$route.path.startsWith('/pokemons/');
      },
    },
  };
  </script>

  <style scoped>
  .header {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 50vh;
  width: 80%;
  }

  .logo {
  margin-bottom: 80px;
  margin-left: 400px; /* Adjust as needed */
  }

  .navigation {
  display: flex;
  justify-content: center; /* Centers the links horizontally */
  width: 50%; /* Takes full width of the parent */
  }

  .nav-link {
  font-size: 1.5rem;
  text-decoration: none;
  color: #333;
    /* Adds horizontal spacing between links */
  transition: color 0.3s ease;
  margin-bottom: 200px;
  margin-left: 400px; 
  }

  .nav-link:hover {
  color: #666;
  
  }
 </style>