<template>
  <div class="list-container">
    <!--titulo lista-->
    <h2>Videojuegos</h2>
    <table class="videogame-table">
      <thead>
        <tr>
          <!--Encabezados de la lista-->
          <th>Nombre</th>
          <th>Plataforma</th>
          <th>Estado</th>
          <th>Puntaje</th>
          <th>Más info</th>
        </tr>
      </thead>
      <tbody>
        <!--Mostramos los videojuegos en las filas de la lista-->
        <tr v-for="game in videogames" :key="game.name">
          <td>{{ game.name }}</td>
          <td>{{ game.platform }}</td>
          <td>{{ game.status }}</td>
          <td>{{ game.rating }}</td>
          <td><button @click="$emit('show-details', game)" class="info-button">+</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    videogames: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
.list-container {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

h2 {
  color: #333;
  text-align: center;
}

.videogame-table {
  width: 100%;
  border-collapse: collapse;
}

.videogame-table th, .videogame-table td {
  border: 1px solid #ddd;
  padding: 8px;
}

.videogame-table th {
  background-color: #f2f2f2;
  text-align: left;
}

.info-button {
  background-color: #51e676;
  color: white;
  padding: 5px 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.info-button:hover {
  background-color: #21f01a;
}
</style>
