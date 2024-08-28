<template>
  <!-- para habilitar un componente de las practicas solo debe quitar el comentario y hab el import del componente -->
  <v-container>
    <!-- <PracticaOne/>
    <div class="btn-container">
      <Boton @click="enviarAlert" nombre="enviar" type="submit" class="success"/> 
    </div>
   
     <CardNoticias
  v-for="items in noticias"
  :key="items.id"
  :id="items.id"
  :title="items.title"
  :body="items.body"
 @accionEliminar="eliminarnoticia"
  />  -->
<GamexRaya/>
  
  </v-container>


</template>

<script setup lang="ts">
import GamexRaya from './Games/GamexRaya.vue';
// import CardNoticias from './CardNoticias.vue';
// import Boton from './Boton.vue';
// import PracticaOne from './PracticaOne.vue';
// import { ref } from 'vue';

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
// const enviarAlert = () =>{
//   alert('Gracias por enviarme 100$')
// }




</script>

<style scoped>
.btn-container{
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 1rem;
    margin: 1rem;
    gap: 0.5rem;
  }
</style>