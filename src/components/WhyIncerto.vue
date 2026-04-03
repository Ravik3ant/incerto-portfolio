<template>
  <section>
    <div class="section-inner">
      <div class="section-label">{{ label }}</div>
      <div class="section-body reveal">
        <div class="grid">
          <div
            v-for="(item, i) in items"
            :key="i"
            class="card"
            :class="{ 'is-open': open === i }"
            @click="toggle(i)"
          >
            <div class="card-head">
              <span class="card-num">{{ String(i + 1).padStart(2, '0') }}</span>
              <h3 class="card-title">{{ item.title }}</h3>
              <span class="card-toggle">{{ open === i ? '−' : '+' }}</span>
            </div>
            <div v-show="open === i" class="card-body">
              <p>{{ item.desc }}</p>
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
  items?: { title: string; desc: string }[];
}>(), {
  label: '§ Why Incerto',
  items: () => [
    {
      title: 'I focus on problems where standard approaches break.',
      desc: 'Most AI teams optimize for speed. Incerto is optimizing for sustained intelligence over long horizons, which needs different memory and reasoning architecture.'
    },
    {
      title: 'I think in systems.',
      desc: 'I model first, then optimize. I care about invariants, failure modes, and compounding behavior.'
    },
    {
      title: 'Ambiguity doesn\'t stop me.',
      desc: 'My micro-scale PneuNet work had almost no prior literature. I built from first principles and still produced usable design direction.'
    }
  ]
});

const open = ref<number | null>(null);

function toggle(i: number) {
  open.value = open.value === i ? null : i;
}
</script>

<style scoped>
.grid {
  display: flex;
  flex-direction: column;
  border: 1px solid var(--border);
}

.card {
  padding: 20px 24px;
  border-bottom: 1px solid var(--border);
  cursor: pointer;
  transition: background 0.2s, border-left-color 0.2s;
  border-left: 2px solid transparent;
}

.card:last-child { border-bottom: none; }

.card:hover { background: var(--bg-alt); }

.card.is-open {
  background: var(--bg-alt);
  border-left-color: var(--accent);
}

.card-head {
  display: flex;
  align-items: center;
  gap: 16px;
}

.card-num {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  color: var(--accent);
  letter-spacing: 0.1em;
}

.card-title {
  flex: 1;
  font-size: 0.97rem;
  font-weight: 600;
  line-height: 1.3;
}

.card-toggle {
  font-family: 'JetBrains Mono', monospace;
  font-size: 1rem;
  color: var(--muted);
  width: 24px;
  text-align: center;
}

.card-body {
  margin-top: 12px;
  padding-left: 40px;
}

.card-body p {
  font-size: 0.86rem;
  line-height: 1.65;
  color: #3f4846;
  max-width: 500px;
}
</style>
