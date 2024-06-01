<template>
    <div class="detail-container">
        <!--Titulo-->
      <h2>Detalles del Videojuego</h2>
      <!--Mostramos los detalles del videojuego selecionado-->
      <div class="detail-item"><strong>Nombre:</strong> {{ game.name }}</div>
      <div class="detail-item"><strong>Plataforma:</strong> {{ game.platform }}</div>
      <div class="detail-item"><strong>Estado:</strong> {{ game.status }}</div>
      <div class="detail-item"><strong>Puntaje:</strong> {{ game.rating }}</div>
      <button @click="$emit('close')" class="close-button">Cerrar</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      game: {
        type: Object,
        required: true
      }
    }
  };
  </script>
  
  <style scoped>
  .detail-container {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    max-width: 400px;
    width: 100%;
  }
  
  h2 {
    color: #333;
    text-align: center;
  }
  
  .detail-item {
    margin-bottom: 10px;
  }
  
  .close-button {
    display: block;
    background-color: #51e676;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin: 0 auto;
  }
  
  .close-button:hover {
    background-color: #21f01a;
  }
  </style>
