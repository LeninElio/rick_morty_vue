<script setup>
import { FwbAvatar } from 'flowbite-vue'
const props = defineProps({
  character: {
    type: Object,
    required: true
  }
})
</script>

<template>
    <div class="flex justify-center space-x-4 m-3">
      <fwb-avatar size="xl" bordered :img="character.image" rounded />
    </div>
</template>
  
<style>
</style>