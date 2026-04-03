<template>
  <div class="ticker-wrap">
    <div class="ticker-track">
      <span v-for="(item, i) in doubled" :key="i" class="ticker-item">
        {{ item }} <span class="ticker-dot">·</span>
      </span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = withDefaults(defineProps<{
  items?: string[];
}>(), {
  items: () => [
    'BITS Hyderabad',
    'M.Sc. Physics + B.E. EEE',
    'AI Engineer @ Made For Planet',
    'Research · Micro-Scale Soft Robotics',
  ]
});

const doubled = computed(() => [...props.items, ...props.items, ...props.items]);
</script>

<style scoped>
.ticker-wrap {
  background: var(--ink);
  color: var(--bg);
  overflow: hidden;
  padding: 16px 0;
  transform: rotate(-1deg) scale(1.2) translateY(-1.5rem);
  position: relative;
  z-index: 10;
  margin-bottom: 8px;
  border-top: 1px solid rgba(255, 255, 255, 0.08);
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.ticker-track {
  display: flex;
  animation: scroll 25s linear infinite;
  width: max-content;
}

.ticker-item {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.76rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  white-space: nowrap;
  padding: 0 8px;
}

.ticker-dot {
  color: var(--accent-light);
  margin: 0 12px;
}

@keyframes scroll {
  from { transform: translateX(0); }
  to { transform: translateX(-33.333%); }
}
</style>
