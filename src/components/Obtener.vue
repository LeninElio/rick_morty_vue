<script setup>
import { ref, onMounted } from 'vue'
import { FwbCard } from 'flowbite-vue'
import axios from 'axios'
import Modal from './Modal.vue'

const url = 'https://rickandmortyapi.com/api/character'
const characters = ref([])

const getPosts = async () => {
  try {
    const response = await axios.get(url)
    characters.value = response.data.results
  } catch (error) {
    console.log(error)
  }
}

onMounted(() => getPosts())

</script>

<template>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 m-8">
    <fwb-card v-for="character in characters" :key="character.id" :img-alt="character.name" :img-src="character.image" variant="horizontal">
      <div class="p-5">
        <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
          {{ character.name }}
        </h5>
        <p class="font-normal text-gray-700 dark:text-gray-400">
          Género: {{ character.gender }}
        </p>
        <p class="font-normal text-gray-700 dark:text-gray-400">
          Ubicación: {{ character.location.name }}
        </p>
        <p class="font-normal text-gray-700 dark:text-gray-400">
          Estado: {{ character.status }}
        </p>
        
        <Modal :character="character"/>
      </div>
    </fwb-card>
  </div>

</template>


<style scoped>

</style>
