<template>
    <v-card
    class="mx-auto" 
    prepend-icon="$vuetify"
    width="600"
    color="#455A64"
  >
    <template v-slot:title>
      <span >{{ title }}</span>
    </template>

    <v-card-text class="bg-surface-light pt-4">
      {{ body }}
    </v-card-text>
    <v-card-actions>
        <Boton 
        nombre ="Eliminar"
         class="danger"
         @click="emit('accionEliminar',id)"
        />
    </v-card-actions>
  </v-card>
  <br>
</template>

<script setup lang="ts">
import Boton from './Boton.vue'

//type TYPE_NOTICIA = {id:'',title:'',body:''};
const emit = defineEmits(['accionEliminar'])
defineProps({id:{
    type:Number
  },
 title:{
    type:String,
    required:true

 },
 body:{
    type:String,
    required:true
 } 
  })
</script>

<style scoped>

</style>