<template>
  <section>
    <div class="section-inner">
      <div class="section-label">{{ label }}</div>
      <div class="section-body reveal">
        <div class="statement-list">
          <div v-for="(item, i) in items" :key="i" class="statement">
            <p class="statement-text" v-html="item.text" />
            <span v-if="item.note" class="statement-note">{{ item.note }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
withDefaults(defineProps<{
  label?: string;
  items?: { text: string; note?: string }[];
}>(), {
  label: '§ Why This',
  items: () => [
    {
      text: 'I ship in ambiguity: frame fast, test hard, update from evidence.',
      note: '[ first principles + execution ]'
    },
    {
      text: 'I am not choosing between research and product. I build systems that survive contact with reality.',
      note: '[ physics + AI + product ]'
    },
  ]
});
</script>

<style scoped>
.statement-list {
  display: flex;
  flex-direction: column;
  gap: 28px;
}

.statement {
  opacity: 0;
  transform: translateY(16px);
  animation: lineIn 0.55s ease forwards;
}

.statement:nth-child(1) { animation-delay: 0.05s; }
.statement:nth-child(2) { animation-delay: 0.12s; }
.statement:nth-child(3) { animation-delay: 0.19s; }

.statement {
  max-width: 640px;
  padding: 12px 0 14px;
  border-bottom: 1px solid var(--border);
}

.statement:last-child { border-bottom: none; }

.statement-text {
  font-size: clamp(1.1rem, 1.8vw, 1.4rem);
  font-weight: 500;
  line-height: 1.5;
  color: var(--ink);
}

.statement-text :deep(em) {
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  font-weight: 400;
  color: var(--accent);
}

.statement-note {
  display: block;
  margin-top: 6px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.72rem;
  color: var(--muted);
  letter-spacing: 0.02em;
}

@keyframes lineIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
