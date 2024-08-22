<template>
<v-container>
  <!-- <PracticaOne/> -->
  <!-- <Boton nombre="enviar" type="submit" class="success"/> -->
  <!-- <CardNoticias
  v-for="items in noticias"
  :key="items.id"
  :id="items.id"
  :title="items.title"
  :body="items.body"
 @accionEliminar="eliminarnoticia"
  /> -->

  <Casilla/>
</v-container>

  
</template>

<script setup lang="ts">
import Casilla from './Games/Casilla.vue';


// import CardNoticias from './CardNoticias.vue';
// import Boton from './Boton.vue';
// import PracticaOne from './PracticaOne.vue';
 //import { ref } from 'vue';

// const noticias = ref([
// {
//         "id": 1,
//         "title": "Venezuela logra un acuerdo histórico con el FMI",
//         "body": "Caracas y el Fondo Monetario Internacional han alcanzado un acuerdo preliminar para la reestructuración de la deuda, lo que podría abrir las puertas a nuevas inversiones y un crecimiento económico sostenido."
//     },
//     {
//         "id": 2,
//         "title": "Aumentan los casos de COVID-19 en Barquisimeto",
//         "body": "Las autoridades sanitarias han reportado un incremento en el número de contagios por coronavirus en la ciudad, por lo que se exhorta a la población a mantener las medidas de bioseguridad."
//     },
//     {
//         "id": 3,        
//         "title": "Inauguran nueva línea de metro en Caracas",
//         "body": "El presidente Nicolás Maduro encabezó la inauguración de la nueva línea del Metro de Caracas, que conectará a varios municipios del Área Metropolitana y beneficiará a millones de usuarios."
//     }
// ]);

// const eliminarnoticia = (id:Number)=>{
//  noticias.value = noticias.value.filter(x =>x.id !==id);

// }


</script>
