<template>
  <div id="app" class="app-container">
    <!--Titulo-->
    <h1>Administración de Videojuegos</h1>
    <div class="content">
      <!--Componente de registro-->
      <RegisterForm @add-videogame="addVideogame" />
      <!--componente  del filtro-->
      <FilterForm @filter-videogames="filterVideogames" />
      <!--Componente de la lista de juegos registrados-->
      <VideogameList :videogames="filteredVideogames" @show-details="showDetails" />
      <!--Componente que muestra detalle del juego selecionado-->
      <VideogameDetail v-if="selectedGame" :game="selectedGame" @close="selectedGame = null" />
    </div>
  </div>
</template>

<script>
import RegisterForm from './components/RegisterForm.vue';
import FilterForm from './components/FilterForm.vue';
import VideogameList from './components/VideogameList.vue';
import VideogameDetail from './components/VideogameDetail.vue';

export default {
  components: {
    RegisterForm,
    FilterForm,
    VideogameList,
    VideogameDetail
  },
  data() {
    return {
      videogames: [],//Lista Videosjuegos registrados
      filteredVideogames: [],//Lista Videojuego filtrado
      selectedGame: null //Videojuego selecionado muestra el detalle
    };
  },
  methods: {
    addVideogame(videogame) {
      //Agregar Videojuego a la lista
      this.videogames.push(videogame);
      this.filteredVideogames = this.videogames;
    },
    //Filtramos la lista segun los criterios de busqueda
    filterVideogames(filters) {
      this.filteredVideogames = this.videogames.filter(vg => {
        return (
          (!filters.name || vg.name.includes(filters.name)) &&
          (!filters.platform || vg.platform === filters.platform) &&
          (!filters.status || vg.status === filters.status)
        );
      });
    },
    //Mostramos los detalles de un videojuego selecionado
    showDetails(game) {
      this.selectedGame = game;
    }
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-image: url('./assets/background.avif');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.app-container {
  background-color:#0f042c;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  max-width: 1200px;
  width: 100%;
  box-sizing: border-box;
}

h1 {
  text-align: center;
  color: #f80caa;
}

.content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
</style>