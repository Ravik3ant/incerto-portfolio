<template>
  <section>
    <div class="section-inner">
      <div class="section-label">{{ label }}</div>
      <div class="section-body reveal">
        <ul class="exp-list">
          <li v-for="(item, i) in items" :key="i" class="exp-item">
            <span class="exp-num">{{ item.num }}</span>
            <div class="exp-content">
              <span class="exp-text">{{ item.text }}</span>
              <span class="exp-note">{{ item.note }}</span>
            </div>
            <span class="exp-tag">{{ item.tag }}</span>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
withDefaults(defineProps<{
  label?: string;
  items?: { num: string; text: string; note: string; tag: string }[];
}>(), {
  label: '§ Work',
  items: () => [
    {
      num: '01',
      text: 'Integrated extended-thinking API for multi-step reasoning in production AI workflows.',
      note: 'Jan 2026-present · AI Engineer @ Made For Planet',
      tag: 'AI'
    },
    {
      num: '02',
      text: 'Added debounce and request guards to search/filter flows to cut redundant API traffic.',
      note: 'Frontend performance and stability improvements',
      tag: 'Frontend'
    },
    {
      num: '03',
      text: 'Redesigned retrieval paths for username and ID lookups with cleaner query structure.',
      note: 'Lower query complexity in core lookup routes',
      tag: 'Backend'
    },
    {
      num: '04',
      text: 'Built a go-to-market strategy framework for Livo.',
      note: 'Aug–Dec 2025 · Market Consultant',
      tag: 'GTM'
    },
    {
      num: '05',
      text: 'Led consulting workstreams at 180 Degrees Consulting.',
      note: 'Aug 2025–present · Consultant & Team Lead',
      tag: 'Strategy'
    }
  ]
});
</script>

<style scoped>
.exp-list {
  list-style: none;
}

.exp-item {
  display: grid;
  grid-template-columns: 32px 1fr auto;
  gap: 16px;
  padding: 18px 0;
  border-bottom: 1px solid var(--border);
  align-items: start;
  transition: padding-left 0.2s, background 0.2s;
}

.exp-item:last-child { border-bottom: none; }
.exp-item:hover {
  padding-left: 8px;
  background: rgba(13, 148, 136, 0.04);
}

.exp-num {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.6rem;
  color: var(--muted);
}

.exp-item:hover .exp-num { color: var(--accent); }

.exp-content {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.exp-text {
  font-size: 0.92rem;
  font-weight: 600;
  line-height: 1.4;
}

.exp-note {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.66rem;
  color: #3d4644;
}

.exp-tag {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.55rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--muted);
  border: 1px solid var(--border);
  padding: 3px 8px;
  transition: border-color 0.2s, color 0.2s;
}

.exp-item:hover .exp-tag {
  border-color: var(--accent);
  color: var(--accent);
}

@media (max-width: 768px) {
  .exp-item { grid-template-columns: 28px 1fr; }
  .exp-tag { display: none; }
}
</style>
