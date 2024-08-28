<template>
    <div div class="container">
        <h2> LA VIEJA</h2>
        <h3 v-show="resultado"> resultado: {{ resultado }}</h3>
    <div class="fila" v-for="(fila,i) in tablero" :key="i">
        
    <Casilla  v-for="(columna,j) in fila" :key="j"
    :figura="columna"
    @click="(changeStateCasilla(i,j))"
    />
    </div>
    <div class="fila">
    <button  class="btns-game"    @click="reset">Reset </button> 
    <button  class="btns-game"  :class="activeTurn(FIGURA.X)" @click="changeTurn(FIGURA.X)">{{ FIGURA.X }}</button>
    <button   class="btns-game"  :class="activeTurn(FIGURA.O)"   @click="changeTurn(FIGURA.O)">{{ FIGURA.O }}</button>
    </div>
   
   </div>
</template>

<script setup lang="ts">
import Casilla from './Casilla.vue';
import { ref,computed } from 'vue';
enum FIGURA{
  X = '❌',
  O = '⚪'
};

const tablero = ref ([
    ['','', ''],
    ['', '',''],
    ['', '',''],
]);

const reset = ()=>{
     tablero.value=[
    ['','', ''],
    ['', '',''],
    ['', '',''],
    ],
    resultado.value= null;
};
const resultado = ref<string | null>(null) 
const turno =ref(FIGURA.X);

const changeStateCasilla =(fila:number ,columna:number)=>{
    if(!tablero.value[fila][columna] && !resultado.value){

        tablero.value[fila][columna] = turno.value;
        turno.value = FIGURA.X === turno.value ? FIGURA.O : FIGURA.X;
    }

    if( verifyVertical(columna,tablero.value[fila][columna]) || verifyHorizontal(fila,tablero.value[fila][columna]) || verifyDiagonal(fila,columna,tablero.value[fila][columna])){
        resultado.value=`Gano${tablero.value[fila][columna]}`
       
    }else 
    
    if(tableFull.value){
        resultado.value ="Empate"
    }
};

const verifyVertical= (columna:number ,figura:string)=>{
    for (let i = 0; i < tablero.value.length; i++) {
        if(tablero.value[i][columna] !== figura){
            return false
        }
        
    }
    return true;
};

const verifyHorizontal= (fila:number ,figura:string)=>{
    for (let i = 0; i < tablero.value.length; i++) {
        if(tablero.value[fila][i] !== figura){
            return false
        }
        
    }
    return true;
};

const verifyDiagonal= (fila:number ,columna: number,figura:string)=>{
    // Diagonal principal (de esquina superior izquierda a esquina inferior derecha)
    if (tablero.value[0][0] === figura && tablero.value[1][1] === figura && tablero.value[2][2] === figura) {
        return true;
    }

    // Diagonal secundaria (de esquina superior derecha a esquina inferior izquierda)
    if (tablero.value[0][2] === figura && tablero.value[1][1] === figura && tablero.value[2][0] === figura) {
        return true;
    }
    return false;

};

const tableEmpty =computed(()=>{
    for (let fila of tablero.value )
    {
        for (let columna of fila){
            if(columna !==''){
                return false
            }
           
            }
   
    }
    return true
});
const tableFull =computed(()=>{
    for (let fila of tablero.value )
    {
        for (let columna of fila){
            if(columna ===''){
                return false
            }
           
            }
   
    }
    return true
});

const changeTurn =(figura:FIGURA)=>{
    if(tableEmpty.value){
        turno.value =figura
    }  
}


const activeTurn = (figura:string)=>{
  return figura === turno.value ? 'btn-activo':'';
} 
 

</script>

<style scoped>
.container{
display: flex;
width: 100%;
height: 90vh;
flex-direction: column;
align-items: center;
justify-content: center;
}
.fila{
    width: 350px;
    display: flex;
}
.btns-game{
  width: auto;
  font-size: 20px;
  background-color: rgb(117, 118, 126);
  border-color: #020202;
  margin: 5px;
  color: #000000;
  padding: 10px;
  border-radius: 20%;
}
.btn-activo{
  background-color:  #33bb33;
}


</style>