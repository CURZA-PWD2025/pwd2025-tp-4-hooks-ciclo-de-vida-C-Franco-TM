<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { profesiones } from '../data/profesiones'

const lista = ref<typeof profesiones | null>(null)

onMounted(() => {
  setTimeout(() => {
    lista.value = profesiones
  }, 3000)
})
</script>

<template>
  <div>
    <h2>Lista</h2>
    <ul v-if="lista">
      <li v-for="profesion in lista" :key="profesion.id">
        <strong>{{ profesion.nombre }}</strong>: {{ profesion.descripcion }}
      </li>
    </ul>
    <p v-else>Cargando...</p>
  </div>
</template>
