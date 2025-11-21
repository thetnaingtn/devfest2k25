<template>
  <div class="random-gopher">
    <img 
      :src="gopherImage" 
      :alt="`Gopher image`"
      class="gopher-img"
    />
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

interface Props {
  gophers: string[]
}

const props = withDefaults(defineProps<Props>(), {
  gophers: () => ['/images/gophers/1.png', '/images/gophers/2.png', '/images/gophers/3.png', '/images/gophers/20.png', '/images/gophers/21.png', '/images/gophers/33.png', '/images/gophers/41.png', '/images/gophers/50.png']
})

// Use current page number to select gopher (ensures unique gopher per slide)
const { $page } = useSlideContext()
const selectedGopher = computed(() => {
  const pageIndex = ($page.value - 1) % props.gophers.length
  return props.gophers[pageIndex]
})

const gopherImage = computed(() => selectedGopher.value)
</script>

<style scoped>
.random-gopher {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 100;
  pointer-events: none;
}

.gopher-img {
  width: 120px;
  height: auto;
  opacity: 0.8;
  transition: opacity 0.3s ease;
}

.gopher-img:hover {
  opacity: 1;
  pointer-events: auto;
  cursor: pointer;
}
</style>