<template>
  <div class="container">
    <div class="indicador" :class="{'rojo': contador < 0, 'verde': contador > 0}"> 
      <div v-if="contador < 0" class="estado">Negativo</div>
      <div v-else-if="contador > 0" class="estado">Positivo</div>
    </div>
    <div class="contador-container">
      <button @click="decremento" class="boton">-</button>
      <span :class="miColor" class="contador">{{ Math.abs(contador) }}</span>
      <button @click="incremento" class="boton">+</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const miColor = ref("negro");
const contador = ref(0);

const decremento = () => {
  contador.value--;
  updateColorAndIndicator();
};

const incremento = () => {
  contador.value++;
  updateColorAndIndicator();
};

const updateColorAndIndicator = () => {
  if (contador.value < 0) {
    miColor.value = 'rojo';
  } else if (contador.value > 0) {
    miColor.value = 'verde';
  } else {
    miColor.value = 'negro';
  }
};
</script>

<style>

.boton {
  font-size: 24px; 
  width: 50px; 
  height: 50px; 
}
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.indicador {
  text-align: center;
  font-weight: bold;
  margin-bottom: 10px;
}

.estado {
  font-size: 18px;
}

.rojo {
  color: red;
}

.verde {
  color: green;
}

.contador-container {
  display: flex;
  align-items: center;
}

span {
  padding: 0 5px;
}
.contador {
  font-size: 50px; 
}
</style>
