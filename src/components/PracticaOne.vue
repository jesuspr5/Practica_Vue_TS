<template>
    <div>
      <!-- Mostrar ahorros, botones para depositar y retirar, listado de movimientos -->
      <div class="btns">
        <h1>${{ ahorros }}</h1>
        <v-btn @click="depositar(100)" rounded color="success">
          Depositar
        </v-btn>
        <br />
        <v-btn @click="retirar(100)" :disabled="disablebtn" rounded color="error">
          Retirar
        </v-btn>
      </div>
  
      <div>
        <v-card class="mx-auto" max-width="400">
          <v-list>
            <v-list-subheader>MOVIMIENTOS</v-list-subheader>
  
            <v-list-item v-for="(item, i) in movimientos" :key="i">
              <template v-slot:prepend>
                <v-icon :icon="item.icon" :color="item.movimiento === 'retirado' ? 'red' : 'green'"></v-icon>
              </template>
              <v-row>
                <v-col>
                <strong :class="{'text-success': item.movimiento === 'depositado', 'text-error': item.movimiento === 'retirado'}">
                  {{ item.movimiento }}:
                </strong> ${{ item.monto }}
              </v-col>
                <v-col>
                  <strong>Saldo Actual:</strong> ${{ item.saldoActual }}
                </v-col>
              </v-row>
              <v-divider></v-divider>
            </v-list-item>
          </v-list>
        </v-card>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { computed, ref } from 'vue';
  
  const ahorros = ref<number>(0);
  const movimientos = ref<IMovimiento[]>([]);
  
  interface IMovimiento {
    monto: number;
    saldoActual: number;
    movimiento: string;
    icon: string;
  }
  
  const depositar = (cantidad: number) => {
    if (typeof cantidad === 'number') {
        ahorros.value += cantidad;
    movimientos.value.push({
      monto: cantidad,
      saldoActual: ahorros.value,
      movimiento: "depositado",
      icon: "mdi-currency-usd"
    });
    }
   
  };
  
  const retirar = (cantidad: number) => {
    if (typeof cantidad === 'number' && ahorros.value >= cantidad) {
        ahorros.value -= cantidad;
    movimientos.value.push({
      monto: -cantidad,
      saldoActual: ahorros.value,
      movimiento: "retirado",
      icon: "mdi-currency-usd"
    });
    };
   
  };
  
  const disablebtn = computed(() => ahorros.value === 0);
  
  </script>
  
  <style scoped>
  .btns {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 1rem;
    margin: 1rem;
    gap: 0.5rem;
  }
  h1 {
    margin-bottom: 1rem;
  }
  </style>
  