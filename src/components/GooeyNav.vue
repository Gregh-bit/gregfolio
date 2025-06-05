<template>
  <div class="relative w-full flex justify-center items-center py-6 gooey-container">
    <div class="flex space-x-4 bg-yellow-300/10 px-6 py-2 rounded-full gooey-bg">
      <button
        v-for="(tab, index) in tabs"
        :key="index"
        @click="setActive(index)"
        class="text-sm font-medium px-4 py-2 rounded-full transition-all duration-300"
        :class="{
          'bg-yellow-300 text-black shadow-md': activeTab === index,
          'text-yellow-300 hover:text-yellow-200': activeTab !== index
        }"
      >
        {{ tab.label }}
      </button>
      <div class="gooey-ball" :style="ballStyle" />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  modelValue: Number
})
const emit = defineEmits(['update:modelValue'])

const tabs = [
  { label: 'Tech Stack' },
  { label: 'Strumenti' },
  { label: 'Istruzione' },
  { label: 'Interessi' }
]

const activeTab = ref(props.modelValue || 0)

function setActive(index) {
  activeTab.value = index
  emit('update:modelValue', index)
}

const ballStyle = computed(() => {
  return {
    transform: `translateX(${activeTab.value * 100}%)`
  }
})
</script>

<style scoped>
.gooey-container {
  filter: url('#gooey-effect');
}
.gooey-bg {
  position: relative;
}
.gooey-ball {
  position: absolute;
  top: 0.25rem;
  left: 0.25rem;
  width: 90px;
  height: 36px;
  background-color: #facc15; /* amber-400 */
  border-radius: 9999px;
  z-index: -1;
  transition: transform 0.3s ease;
}
</style>

<svg width="0" height="0">
  <filter id="gooey-effect">
    <feGaussianBlur in="SourceGraphic" stdDeviation="6" result="blur" />
    <feColorMatrix in="blur" mode="matrix"
      values="1 0 0 0 0  
              0 1 0 0 0  
              0 0 1 0 0  
              0 0 0 20 -10" result="gooey" />
    <feComposite in="SourceGraphic" in2="gooey" operator="atop"/>
  </filter>
</svg>
