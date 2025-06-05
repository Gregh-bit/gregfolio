<template>
  <div class="gooey-nav-container">
    <nav class="gooey-nav">
      <button
        v-for="(tab, index) in tabs"
        :key="index"
        :class="{ active: modelValue === index }"
        @click="emit('update:modelValue', index)"
      >
        {{ tab }}
      </button>
      <div class="gooey"></div>
    </nav>
  </div>
</template>

<script setup>
// eslint-disable-next-line no-undef
const props = defineProps({
  modelValue: Number
})
// eslint-disable-next-line no-undef
const emit = defineEmits(['update:modelValue'])

const tabs = ['Tech Stack', 'Strumenti', 'Istruzione', 'Interessi']
</script>

<style scoped>
.gooey-nav-container {
  display: flex;
  justify-content: center;
  padding: 2rem;
}

.gooey-nav {
  display: flex;
  position: relative;
  background: #facc15; /* Giallo */
  border-radius: 50px;
  padding: 0.5rem;
  filter: url('#goo');
}

.gooey-nav button {
  background: white;
  border: none;
  padding: 0.75rem 1.25rem;
  margin: 0 0.25rem;
  border-radius: 50px;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s ease, color 0.3s ease;
}

.gooey-nav button.active {
  background: #fbbf24; /* Giallo scuro */
  color: white;
}

.gooey {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

svg {
  position: absolute;
  width: 0;
  height: 0;
}
</style>

<!-- Gooey filter -->
<svg>
  <filter id="goo">
    <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
    <feColorMatrix
      in="blur"
      mode="matrix"
      values="
        1 0 0 0 0
        0 1 0 0 0
        0 0 1 0 0
        0 0 0 20 -10"
      result="goo"
    />
    <feComposite in="SourceGraphic" in2="goo" operator="atop" />
  </filter>
</svg>
