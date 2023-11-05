<script setup>

import { ref } from 'vue';
import { FwbButton, FwbModal } from 'flowbite-vue';
import Avatar from './Avatar.vue'

const props = defineProps({
  character: {
    type: Object,
    required: true
  }
})

const isShowModal = ref(false)

function closeModal () {
    isShowModal.value = false
}
function showModal () {
    isShowModal.value = true
}
</script>

<template>
    <fwb-button @click="showModal">
      Mas detalles
    </fwb-button>
    <fwb-modal v-if="isShowModal" @close="closeModal">
        <template #header>
          <div class="flex flex-col items-start font-bold text-gray-800 dark:text-gray-400">
            Infografía de:
            <p class="text-base uppercase leading-relaxed text-gray-800 dark:text-gray-100">
              {{ character.name }}
            </p>
          </div>
        </template>
        <template #body>
          <div class="columns-2">
            <div>
              <Avatar :character="character"/>
            </div>
            <div>
              <p class="text-base leading-relaxed text-gray-800 dark:text-gray-400">
                Estado:
                <span v-if="character.status == 'Alive'" class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  Vivo
                </span>
                <span v-else-if="character.status == 'Dead'" class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  Fallecido
                </span>
                <span v-else class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  Desconocido
                </span>
              </p>
              <p class="text-base leading-relaxed text-gray-800 dark:text-gray-400">
                Especie:
                <span class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  {{ character.species }}
                </span>
              </p>
              <p class="text-base leading-relaxed text-gray-800 dark:text-gray-400">
                Genero:
                <span class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  {{ character.gender }}
                </span>
              </p>
              <p class="text-base leading-relaxed text-gray-800 dark:text-gray-400">
                Origen:
                <span class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  {{ character.origin.name }}
                </span>
              </p>
              <p class="text-base leading-relaxed text-gray-800 dark:text-gray-400">
                Ubicación:
                <span class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  {{ character.location.name }}
                </span>
              </p>
              <p class="text-base leading-relaxed text-gray-800 dark:text-gray-400">
                Episodios en los que aparece:
                <span class="text-base leading-relaxed text-gray-800 dark:text-gray-100">
                  {{ character.episode.length }}
                </span>
              </p>
            </div>
          </div>
        </template>
        <template #footer>
          <div class="flex justify-between">
            <fwb-button @click="closeModal" color="green">
              Cerrar
            </fwb-button>
          </div>
        </template>
    </fwb-modal>

</template>

  
<style scoped>
</style>