<script setup lang="ts">
const powerPointUrl = `${import.meta.env.BASE_URL}TC147_slides.pptx`
</script>

<template>
  <a
    class="powerpoint-download"
    :href="powerPointUrl"
    download="TC147_slides.pptx"
    title="Download PowerPoint (.pptx)"
    aria-label="Download the 16-slide PowerPoint presentation"
    @click.stop
  >PowerPoint</a>
</template>

<style scoped>
.powerpoint-download {
  display: inline-flex;
  align-items: center;
  align-self: center;
  min-height: 32px;
  padding: 4px 8px;
  border-radius: 4px;
  color: inherit;
  font-size: 13px;
  line-height: 1.25;
  text-decoration: none;
}
.powerpoint-download:hover {
  background: #8882;
}
.powerpoint-download:focus-visible {
  outline: 2px solid currentColor;
  outline-offset: 2px;
}
</style>
