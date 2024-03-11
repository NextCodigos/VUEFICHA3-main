<template>
    <!-- Componente que muestra un artículo con su nombre, marca y puntuación -->
    <div class="display">
        <button class="boton">
            {{ cosa.ropa }} ({{ cosa.marca }})
        </button>
        <div class="estrellas">
            <!-- Itera sobre la puntuación y muestra una imagen de estrella por cada punto -->
            <span v-for="index in cosa.nota" :key="index">
                <img src="https://www.html6.es/img/estrella.png" alt="Estrella">
            </span>
        </div>
        <!-- Botón para incrementar la puntuación -->
        <button @click="incrementarNota(cosa.nota,index)">+</button>
    </div>
</template>

<script setup>
const emito = defineEmits('[retorno]');
const incrementarNota = (puntuacion, indice) => {
    // Comunica con el componente padre para actualizar la puntuación
    emito('retorno', puntuacion, indice);
}
const props = defineProps({
    cosa: String, // Propiedad que recibe el nombre, marca y puntuación del artículo
    index: Number // Propiedad que recibe el índice del artículo en la lista
});
</script>

<style scoped>
/* Estilos para el contenedor principal */
.display {
    display: flex; /* Muestra los elementos en línea */
    align-items: center; /* Alinea verticalmente los elementos */
}

/* Estilos para las imágenes de estrellas */
.display img {
    width: 15px; /* Tamaño de las estrellas */
    margin: 1px; /* Espacio entre las estrellas */
}

/* Establece margen a los botones dentro del contenedor principal */
.display button {
    margin-right: 20px;
}

/* Estilos para el botón de artículo */
.boton {
    width: 165px; /* Tamaño del botón de artículo */
}

/* Estilos para el contenedor de estrellas */
.estrellas {
    display: flex; /* Muestra las estrellas en línea */
    align-items: center; /* Alinea verticalmente las estrellas */
    min-width: 125px; /* Establece un ancho mínimo para el contenedor de estrellas */
}
</style>