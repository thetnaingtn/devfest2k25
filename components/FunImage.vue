<template>
  <div class="fun-image" :class="positionClass">
    <img 
      :src="src" 
      :alt="'Fun image'"
      class="fun-img"
    />
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  src: string
  position: 'top-right' | 'bottom-right'
}

const props = withDefaults(defineProps<Props>(), {
  position: 'bottom-right'
})

const positionClass = computed(() => {
  return props.position === 'top-right' ? 'top-right' : 'bottom-right'
})
</script>

<style scoped>
.fun-image {
  position: fixed;
  right: 20px;
  z-index: 100;
  pointer-events: none;
}

.fun-image.top-right {
  top: 20px;
}

.fun-image.bottom-right {
  bottom: 20px;
}

.fun-img {
  width: 120px;
  height: auto;
  opacity: 0.8;
  transition: opacity 0.3s ease;
}

.fun-img:hover {
  opacity: 1;
  pointer-events: auto;
  cursor: pointer;
}
</style>
