<script setup lang="ts">
import { computed, getCurrentInstance, ref, watch } from 'vue'
import { useSlideContext } from '@slidev/client'

type Region = { x: number; y: number; w: number; h: number; at: number; label: string }
type Link = { x: number; y: number; w: number; h: number; href: string; label: string }

const props = withDefaults(defineProps<{
  src: string
  page: number
  title: string
  regions?: Region[]
  links?: Link[]
}>(), { regions: () => [], links: () => [] })

const { $clicks } = useSlideContext()
const src = computed(() => `${import.meta.env.BASE_URL}${props.src.replace(/^\//, '')}`)
const visible = (region: Region) => $clicks.value >= region.at
const prefix = `ppt-${props.page}-${getCurrentInstance()!.uid}`
const artwork = ref('')
const ready = ref(false)
const loadError = ref('')

watch(src, async (url) => {
  ready.value = false
  try {
    const absoluteURL = new URL(url, window.location.href)
    const response = await fetch(absoluteURL)
    if (!response.ok) throw new Error(`Slide image HTTP ${response.status}`)
    const doc = new DOMParser().parseFromString(await response.text(), 'image/svg+xml')
    if (doc.querySelector('parsererror')) throw new Error('Invalid slide artwork')
    const svg = doc.documentElement
    // Each slide and presentation context gets its own glyph/clip identifiers.
    const ids = new Map(Array.from(svg.querySelectorAll('[id]'), el =>
      [el.id, `${prefix}-art-${el.id}`]))
    for (const element of [svg, ...Array.from(svg.querySelectorAll('*'))]) {
      for (const attr of Array.from(element.attributes)) {
        if (attr.name === 'id') attr.value = ids.get(attr.value) || attr.value
        else if ((attr.localName === 'href') && attr.value.startsWith('#'))
          attr.value = `#${ids.get(attr.value.slice(1)) || attr.value.slice(1)}`
        else attr.value = attr.value.replace(/url\(#([^)]*)\)/g,
          (_, id) => `url(#${ids.get(id) || id})`)
      }
    }
    const images: Promise<void>[] = []
    for (const element of Array.from(svg.querySelectorAll('image'))) {
      const href = element.getAttribute('href') || element.getAttributeNS('http://www.w3.org/1999/xlink', 'href')
      if (!href || href.startsWith('#')) continue
      const resolved = new URL(href, absoluteURL).href
      element.setAttributeNS('http://www.w3.org/1999/xlink', 'href', resolved)
      images.push(new Promise((resolve, reject) => {
        const image = new Image()
        image.onload = () => resolve()
        image.onerror = () => reject(new Error('An original PNG did not load'))
        image.src = resolved
      }))
    }
    await Promise.all(images)
    // Inline the slide's paths and original PNG elements. A whole slide rendered
    // as one external SVG <image> can acquire a low-resolution backing texture
    // when Slidev scales its canvas on a high-DPI screen.
    artwork.value = `<symbol id="${prefix}-artwork" viewBox="${svg.getAttribute('viewBox')}">${svg.innerHTML}</symbol>`
    ready.value = true
  }
  catch (error) {
    loadError.value = String(error)
    console.error(error)
  }
}, { immediate: true })
</script>

<template>
  <svg class="ppt-slide" viewBox="0 0 1280 720" role="img" :aria-label="title" data-waitfor="[data-artwork-ready='true']">
    <defs v-html="artwork" />
    <defs>
      <mask :id="`${prefix}-base`" maskUnits="userSpaceOnUse" x="0" y="0" width="1280" height="720">
        <rect width="1280" height="720" fill="white" />
        <rect v-for="(region, index) in regions" :key="index"
          :x="region.x" :y="region.y" :width="region.w" :height="region.h" fill="black" />
      </mask>
      <clipPath v-for="(region, index) in regions" :key="index" :id="`${prefix}-clip-${index}`" clipPathUnits="userSpaceOnUse">
        <rect :x="region.x" :y="region.y" :width="region.w" :height="region.h" />
      </clipPath>
    </defs>
    <rect width="1280" height="720" fill="white" />
    <g v-if="ready" data-artwork-ready="true">
    <use :href="`#${prefix}-artwork`" width="1280" height="720" :mask="regions.length ? `url(#${prefix}-base)` : undefined" />
    <g v-for="(region, index) in regions" :key="index"
      class="ppt-reveal" :data-step="region.at" :data-label="region.label"
      :style="{ opacity: visible(region) ? 1 : 0 }"
      :clip-path="`url(#${prefix}-clip-${index})`">
      <use :href="`#${prefix}-artwork`" width="1280" height="720" />
    </g>
    </g>
    <text v-if="loadError" x="40" y="80" fill="#a00" font-size="24">{{ loadError }}</text>
    <a v-for="(link, index) in links" :key="index" :href="link.href" target="_blank" rel="noopener noreferrer" :aria-label="link.label">
      <title>{{ link.label }}</title>
      <rect :x="link.x" :y="link.y" :width="link.w" :height="link.h" fill="transparent" class="ppt-link" />
    </a>
  </svg>
</template>

<style scoped>
.ppt-slide { display: block; width: 100%; height: 100%; }
.ppt-reveal { transition: opacity 280ms ease-out; }
.ppt-link { cursor: pointer; }
@media print { .ppt-reveal { opacity: 1 !important; transition: none !important; } }
@media (prefers-reduced-motion: reduce) { .ppt-reveal { transition: none; } }
</style>
