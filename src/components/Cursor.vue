<template>
  <div class="cursor" :class="{ grow: isGrown }" :style="{ left: x + 'px', top: y + 'px' }" />
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const x = ref(-100);
const y = ref(-100);
const isGrown = ref(false);

function onMouseEnter() {
  isGrown.value = true;
}

function onMouseLeave() {
  isGrown.value = false;
}

let interactiveEls: Element[] = [];

function onMouseMove(e: MouseEvent) {
  x.value = e.clientX;
  y.value = e.clientY;
}

onMounted(() => {
  document.addEventListener('mousemove', onMouseMove);
  interactiveEls = Array.from(document.querySelectorAll('a, button, .card, .research-item'));
  interactiveEls.forEach((el) => {
    el.addEventListener('mouseenter', onMouseEnter);
    el.addEventListener('mouseleave', onMouseLeave);
  });
});

onUnmounted(() => {
  document.removeEventListener('mousemove', onMouseMove);
  interactiveEls.forEach((el) => {
    el.removeEventListener('mouseenter', onMouseEnter);
    el.removeEventListener('mouseleave', onMouseLeave);
  });
});
</script>

<style scoped>
.cursor {
  position: fixed;
  width: 14px;
  height: 14px;
  background: #f05d5e;
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%, -50%);
  transition: width 0.18s ease, height 0.18s ease;
  mix-blend-mode: difference;
}

.cursor::after {
  content: '';
  position: absolute;
  inset: -9px;
  border: 1px solid rgba(240, 93, 94, 0.55);
  border-radius: 999px;
}

.cursor.grow {
  width: 20px;
  height: 20px;
}
</style>
