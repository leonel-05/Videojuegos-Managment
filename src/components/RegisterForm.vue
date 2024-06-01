<template>
  <div class="form-container">
    <h2>Nuevo videojuego</h2>
    <form @submit.prevent="registerVideogame">
      <!--Campo donde se ingresa el nombre del Videojuego-->
      <div class="form-group">
        <label>Nombre:</label>
        <input v-model="videogame.name" type="text" required />
      </div>
      <!--Campo donde selecionamos la plataforma del Videojuego-->
      <div class="form-group">
        <label>Plataforma:</label>
        <select v-model="videogame.platform" required>
          <option>PC</option>
          <option>PlayStation</option>
          <option>Xbox One</option>
        </select>
      </div>
      <!--Campo para selecionar el estado-->
      <div class="form-group">
        <label>Estado:</label>
        <select v-model="videogame.status" required>
          <option>Pendiente</option>
          <option>Jugando</option>
          <option>Completado</option>
        </select>
      </div>
      <!--Campo para ingresar un puntaje-->
      <div class="form-group">
        <label>Puntaje:</label>
        <input v-model="videogame.rating" type="number" min="1" max="10" />
      </div>
      <!--Mensaje de error por datos invalidos-->
      <div v-if="error" class="error">{{ error }}</div>
      <button type="submit" class="submit-button">Registrar videojuego</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      videogame: {
        name: '',
        platform: '',
        status: '',
        rating: ''
      },
      error: null
    };
  },
  methods: {
    //Validamos todos los datos ingresados y emitimos el evento para egregar el Videojuego
    registerVideogame() {
      this.error = null;
      if (!this.videogame.name || !this.videogame.platform || !this.videogame.status) {
        this.error = 'Todos los campos son requeridos, excepto el puntaje.';
        return;
      }
      if (this.videogame.rating && (this.videogame.rating < 1 || this.videogame.rating > 10)) {
        this.error = 'El puntaje debe estar entre 1 y 10.';
        return;
      }
      this.$emit('add-videogame', { ...this.videogame });
      this.videogame = { name: '', platform: '', status: '', rating: '' };
    }
  }
};
</script>

<style scoped>
.form-container {
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

.error {
  color: red;
  margin-top: 10px;
}
</style>