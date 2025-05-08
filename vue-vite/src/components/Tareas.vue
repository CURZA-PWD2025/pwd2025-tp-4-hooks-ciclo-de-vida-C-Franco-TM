<script setup lang="ts">
import { ref, onBeforeUpdate, onUpdated } from 'vue'

const input = ref('')
const listaTareas = ref([
  { texto: 'comprar harina', pintada: true },
  { texto: 'comprar papel higiénico', pintada: true }
])

function addTarea() {
  if (input.value.trim()) {
    listaTareas.value.push({
      texto: input.value.trim(),
      pintada: false
    })
    input.value = ''
  }
}

onBeforeUpdate(() => {
  console.log('Lista aún no modificada')
  listaTareas.value.forEach(t => t.pintada = true)
})

onUpdated(() => {
  console.log('Lista modificada')
})
</script>

<template>
  <div>
    <h2>Tareas</h2>
    <input v-model="input" @keyup.enter="addTarea" />
    <ul>
      <li
        v-for="(tarea, i) in listaTareas"
        :key="i"
        :class="{ pintada: tarea.pintada }"
      >
        {{ tarea.texto }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
.pintada {
  color: red;
  font-weight: bold;
}
</style>
