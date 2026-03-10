<script setup lang="ts">
import {ref, computed}from "vue";

const P = ref<persona>({
  nombre:'Christian',
  apellido:'Macias'
});

interface persona {
  nombre: string;
  apellido: string;
}

const nombre = ref<string>('Christian');
const apellido = ref<string>('Macias');

const nombreCompleto = computed(() => {
  return `${P.value.nombre} ${P.value.apellido}`;
});

</script>

<template>
  <div>
    <from action="">
      <input type="text" v-model="P.nombre">
      <input type="text" v-model="P.apellido">
      <h1>El nombre completo es: {{nombreCompleto}}</h1>
    </from>
  </div>
</template>

