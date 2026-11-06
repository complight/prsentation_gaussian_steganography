<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  src: string
  page: number
  title: string
}>()

const src = computed(() => `${import.meta.env.BASE_URL}${props.src.replace(/^\//, '')}`)
</script>

<template>
  <img
    class="ppt-image"
    :src="src"
    :alt="`Slide ${page} of 16: ${title}`"
    width="1920"
    height="1080"
    draggable="false"
  >
</template>

<style scoped>
.ppt-image {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: contain;
}
</style>
