<template>
  <div class="contenedor">
    <h1>Conversor de Temperatura</h1>
    <div class="conversor">
      <div class="campo">
        <label for="celsius">Grados Celsius:</label>
        <input 
          type="number" 
          id="celsius" 
          v-model.number="celsius" 
          placeholder="Ingrese temperatura en °C"
          step="0.1"
        >
      </div>
      
      <div class="resultados">
        <p :class="temperaturaClase">
          {{ fahrenheit.toFixed(2) }} °F
        </p>
        <p :class="temperaturaClase">
          {{ kelvin.toFixed(2) }} K
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      celsius: 0
    }
  },
  computed: {
    fahrenheit() {
      return (this.celsius * 9/5) + 32;
    },
    kelvin() {
      return this.celsius + 273.15;
    },
    temperaturaClase() {
      if (this.celsius <= 0) return 'azul';
      if (this.celsius < 15) return 'magenta';
      return 'rojo';
    }
  }
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f5f5f5;
}

.contenedor {
  background: white;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  max-width: 500px;
  width: 100%;
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 2rem;
}

.campo {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: bold;
  color: #555;
}

input[type="number"] {
  width: 100%;
  padding: 0.8rem;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 1rem;
  box-sizing: border-box;
}

.resultados {
  margin-top: 2rem;
}

.resultados p {
  font-size: 1.2rem;
  margin: 0.5rem 0;
  padding: 0.8rem;
  border-radius: 4px;
  background-color: #f9f9f9;
}

.azul {
  color: #1a73e8;
}

.magenta {
  color: #d81b60;
}

.rojo {
  color: #e53935;
}
</style>
