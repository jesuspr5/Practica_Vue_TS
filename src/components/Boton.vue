<template>
    <v-btn  
    :type="type"
    :disabled="disabled"
    rounded
    :class="asignarClase" >
    {{ nombre }}
    </v-btn>
</template>

<script setup lang="ts">
import { computed } from 'vue';
type TYPE_BUTTON = 'button'|'submit'|'reset';
type TYPE_CLASS = 'Primary'| 'success'| 'warning'| 'error'|'danger';
const props =defineProps(
{
    nombre:{
        type:String,
        required:true

    },
    disabled:{
        type:Boolean,
        default:false
    },
    type:{ 
        type :String as ()=> TYPE_BUTTON,
        validator(value:string){
            return ['button','submit','reset'].includes(value) 
           } ,
           default:'button' 

    },
    class:{
        type:String as ()=>TYPE_CLASS,
        default:'primary'
        
    }
},
);
const asignarClase = computed(() => {
    if(props.class){
       return `btn btn-${props.class}`
    }
  
});
</script>

<style scoped>

</style>