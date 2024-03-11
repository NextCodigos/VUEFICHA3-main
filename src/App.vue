<template>
  <!-- Componente padre que muestra una lista de artículos -->
  <div>
    <!-- Recorre la lista de artículos y envía cada artículo como prop al componente FichaVue -->
    <div v-for="(cosa, index) in cosas" :key="index">
      <FichaVue :cosa="cosa" :index="index" @retorno="retorno"/>
    </div>
  </div>
</template>
  
<script setup>
  // Importa el componente FichaVue y la lista de artículos desde datos.js
  import FichaVue from './components/Ficha.vue'
  import cosas from "./assets/datos"

  // Función que recibe la puntuación actual y el índice del artículo, y actualiza la puntuación
  const retorno = (puntuacion, indice) => {
    if (puntuacion >= 6) {
      cosas.value[indice].nota = 1; // Reinicia la puntuación si es mayor o igual a 6
    } else {
      cosas.value[indice].nota = puntuacion + 1; // Incrementa la puntuación si es menor a 6
    }
  }
</script>

<style scoped></style>