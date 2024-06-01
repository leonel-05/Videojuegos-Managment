<template>
    <div class="filter-container">
      <h2>Filtrar videojuegos</h2>
      <form @submit.prevent="applyFilter">
        <div class="form-group">
            <!--Campo para filtrar por nombre-->
          <label>Nombre:</label>
          <input v-model="filters.name" type="text" />
        </div>
        <div class="form-group">
            <!--Campo para filtrar por la plataforma-->
          <label>Plataforma:</label>
          <select v-model="filters.platform">
            <option value="">Todas</option>
            <option>PC</option>
            <option>PlayStation</option>
            <option>Xbox One</option>
          </select>
        </div>
        <div class="form-group">
            <!--Campo para filtrar por el estado-->
          <label>Estado:</label>
          <select v-model="filters.status">
            <option value="">Todos</option>
            <option>Pendiente</option>
            <option>Jugando</option>
            <option>Completado</option>
          </select>
        </div>
        <button type="submit" class="submit-button">Aplicar filtro</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        filters: {
          name: '',
          platform: '',
          status: ''
        }
      };
    },
    methods: {
        //Emitimos el evento para aplicar el filtro ingresado
      applyFilter() {
        this.$emit('filter-videogames', { ...this.filters });
      }
    }
  };
  </script>
  
  <style scoped>
  .filter-container {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  h2 {
    color: #333;
    text-align: center;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    color: #333;
  }
  
  input, select {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .submit-button {
    display: inline-block;
    background-color: #51e676;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .submit-button:hover {
    background-color: #21f01a;
  }
  </style>