<template>
 <div>
    <button>
{{ figura }}
        </button>
 </div>
        
  
</template>

<script setup lang="ts">
defineProps({
    figura:String
})

</script>

<style scoped>
button{
width: 100px;
height: 100px;
font-size: 50px;
background-color: rgb(83, 87, 80) ;
border-color: rgb(8, 8, 8);
margin: 5px;
cursor: pointer;
}
</style>