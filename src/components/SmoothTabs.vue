<template>
  <div class="w-full max-w-xl mx-auto">
    <div class="relative flex border-b border-gray-300 dark:border-gray-700">
      <button
        v-for="(tab, i) in tabs"
        :key="tab.label"
        @click="selected = i"
        class="relative px-4 py-2 text-sm font-medium text-gray-700 dark:text-gray-200"
      >
        {{ tab.label }}
      </button>
      <motion.div
        class="absolute bottom-0 h-[2px] bg-yellow-400"
        :style="{ left: underlineLeft, width: underlineWidth }"
        transition="{ type: 'spring', stiffness: 400, damping: 40 }"
        layout
      />
    </div>

    <div class="py-6 text-sm text-gray-600 dark:text-gray-300 min-h-[80px]">
      <transition name="fade" mode="out-in">
        <div :key="tabs[selected].label">
          <component :is="tabs[selected].component" />
        </div>
      </transition>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue'
import { motion } from 'motion-v'

// Componenti contenuto tab (puoi cambiarli con contenuto diretto o slot)
const TechStack = {
  template: `<div><strong>Vue.js</strong>, Tailwind, HTML, CSS, JavaScript, Python (avanzato)</div>`
}
const Tools = {
  template: `<div>GitHub, Canva, Photoshop, DaVinci Resolve, Office, ecc.</div>`
}
const Education = {
  template: `<div>Studente universitario, ambito tech/design.</div>`
}
const Interests = {
  template: `<div>Musica, editing, 3D printing, creatività digitale.</div>`
}

const tabs = [
  { label: 'Tech Stack', component: TechStack },
  { label: 'Strumenti', component: Tools },
  { label: 'Istruzione', component: Education },
  { label: 'Interessi', component: Interests }
]

const selected = ref(0)
const underlineLeft = ref('0px')
const underlineWidth = ref('0px')

onMounted(() => {
  nextTick(updateUnderline)
})

watch(selected, () => {
  nextTick(updateUnderline)
})

function updateUnderline() {
  const buttons = document.querySelectorAll('button')
  const el = buttons[selected.value]
  if (el) {
    const rect = el.getBoundingClientRect()
    const parentRect = el.parentElement.getBoundingClientRect()
    underlineLeft.value = `${rect.left - parentRect.left}px`
    underlineWidth.value = `${rect.width}px`
  }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
