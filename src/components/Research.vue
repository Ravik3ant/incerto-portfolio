<template>
  <section>
    <div class="section-inner">
      <div class="section-label">{{ label }}</div>
      <div class="section-body reveal">
        <div class="research-list">
          <div
            v-for="(item, i) in items"
            :key="i"
            class="research-item"
            :class="{ 'is-open': open === i }"
            @click="toggle(i)"
          >
            <div class="research-head">
              <span class="research-tag">{{ item.tag }}</span>
              <h3 class="research-title">{{ item.title }}</h3>
              <span class="research-toggle">{{ open === i ? '−' : '+' }}</span>
            </div>

            <p class="research-brief">{{ item.brief }}</p>

            <div v-show="open === i" class="research-detail">
              <div class="insight">
                <span class="insight-label">Key Insight</span>
                <p>{{ item.insight }}</p>
              </div>
              <p class="output">{{ item.output }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

withDefaults(defineProps<{
  label?: string;
  items?: { tag: string; title: string; brief: string; insight: string; output: string }[];
}>(), {
  label: '§ Research',
  items: () => [
    {
      tag: 'Soft Robotics',
      title: 'Micro-Scale PneuNet Optimization',
      brief: 'Derived actuator geometry at ~100 um scale from first principles where almost no literature exists.',
      insight: 'At this scale, mass and gravity terms can be deprioritized. Treating the domain as a different regime cut design noise and made optimization tractable.',
      output: 'Output: model-driven geometry shortlist for micro-scale prototypes.'
    },
    {
      tag: 'Computational Physics',
      title: 'Chladni Pattern Reproduction',
      brief: 'Built simulations to reproduce Chladni plate modes and used them in instructional sessions.',
      insight: 'When outputs diverged, I traced each failure to violated physical assumptions rather than tuning parameters blindly.',
      output: 'Output: reproducible pattern simulations used in peer teaching.'
    }
  ]
});

const open = ref<number | null>(0);

function toggle(i: number) {
  open.value = open.value === i ? null : i;
}
</script>

<style scoped>
.research-list {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.research-item {
  padding: 24px;
  border: 1px solid var(--border);
  cursor: pointer;
  transition: border-color 0.2s, background 0.2s, transform 0.25s;
}

.research-item:hover,
.research-item.is-open {
  border-color: var(--accent);
  background: var(--bg-alt);
}

.research-item:hover {
  transform: translateY(-2px);
}

.research-head {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  margin-bottom: 8px;
}

.research-tag {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.58rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--accent);
  border: 1px solid var(--accent);
  padding: 3px 8px;
  flex-shrink: 0;
}

.research-title {
  flex: 1;
  font-size: 1.05rem;
  font-weight: 600;
  line-height: 1.3;
}

.research-toggle {
  font-family: 'JetBrains Mono', monospace;
  font-size: 1rem;
  color: var(--muted);
}

.research-brief {
  font-size: 0.85rem;
  line-height: 1.6;
  color: var(--muted);
  max-width: 540px;
}

.research-detail {
  margin-top: 16px;
  padding-top: 16px;
  border-top: 1px solid var(--border);
}

.insight {
  padding-left: 12px;
  border-left: 2px solid var(--accent);
}

.insight-label {
  display: block;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.58rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 6px;
}

.insight p {
  font-size: 0.85rem;
  line-height: 1.7;
  color: var(--muted);
}

.output {
  margin-top: 12px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.66rem;
  letter-spacing: 0.04em;
  color: #24312e;
}
</style>
