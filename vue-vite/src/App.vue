<script setup lang="ts">
import { ref } from 'vue'
import Lista from './components/Lista.vue'
import Tareas from './components/Tareas.vue'
import DimensionComponente from './components/DimensionComponente.vue'

const componenteActivo = ref('Lista')

const componentes: Record<string, any> = {
  Lista,
  Tareas,
  DimensionComponente
}
</script>

<template>
  <h1>Componentes</h1>

  <div>
    <button @click="componenteActivo = 'Lista'">Lista</button>
    <button @click="componenteActivo = 'Tareas'">Tareas</button>
    <button @click="componenteActivo = 'DimensionComponente'">DimensionComponente</button>
  </div>

  <component :is="componentes[componenteActivo]" />
</template>


<style scoped>
button {
  margin: 5px;
  padding: 8px 12px;
  background-color: #c0392b;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #e74c3c;
}

button:focus {
  outline: none;
  background-color: #a93226;
}
</style>
