<script setup lang="ts">
import { ref, computed } from 'vue'
import { useFetch } from '@vueuse/core'

const { data } = useFetch('https://api.jikan.moe/v4/anime/1535/characters').json()

const nombre = ref('')

const personaje = computed(() => {
  if (!nombre.value) return null
  return data.value?.data?.find((e: any) =>
    e.character.name.toLowerCase().includes(nombre.value.toLowerCase())
  )
})
</script>

<template>
  <div>
    <h1>Death Note</h1>

    <input v-model="nombre" placeholder="Escribe un personaje" />

    <div v-if="personaje">
      <img :src="personaje.character.images.jpg.image_url" />
      <p>Nombre: {{ personaje.character.name }}</p>
      <p>Rol: {{ personaje.role }}</p>
      <p>Imagen: {{ personaje.character.images.jpg.image_url }}</p>
      <p>Actor: {{ personaje.voice_actors[0].person.name }}</p>
    </div>
  </div>
</template>