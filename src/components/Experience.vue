<template>
  <section>
    <div class="section-inner">
      <div class="section-label">{{ label }}</div>
      <div class="section-body reveal">
        <ul class="exp-list">
          <li
            v-for="(item, i) in items"
            :key="i"
            class="exp-item"
            :class="{ 'is-open': visibleSteps(i) > 0 }"
            @click="advance(i)"
            @mouseenter="hoveredIndex = i"
            @mouseleave="hoveredIndex = null"
          >
            <span class="exp-num">{{ item.num }}</span>
            <div class="exp-content">
              <span class="exp-role">{{ item.role }}</span>
              <span class="exp-summary">{{ item.summary }}</span>

              <div class="exp-brief" :class="{ 'is-visible': hoveredIndex === i && visibleSteps(i) === 0 }">
                <p>{{ item.brief }}</p>
              </div>

              <div class="par" :class="{ 'is-visible': visibleSteps(i) > 0 }">
                <span class="exp-text" :class="{ 'is-revealed': visibleSteps(i) >= 1 }"><strong>P</strong> {{ item.problem }}</span>
                <span class="exp-text" :class="{ 'is-revealed': visibleSteps(i) >= 2 }"><strong>A</strong> {{ item.action }}</span>
                <span class="exp-text" :class="{ 'is-revealed': visibleSteps(i) >= 3 }"><strong>R</strong> {{ item.result }}</span>
                <span class="exp-hint" v-if="visibleSteps(i) < 3">{{ visibleSteps(i) }}/3 - click for more</span>
                <span class="exp-hint done" v-else>full story - click to collapse</span>
              </div>

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
import { reactive, ref } from 'vue';

withDefaults(defineProps<{
  label?: string;
  items?: { num: string; role: string; summary: string; brief: string; problem: string; action: string; result: string; note: string; tag: string }[];
}>(), {
  label: '§ Work',
  items: () => [
    {
      num: '01',
      role: 'AI Engineer @ Made For Planet',
      summary: 'Integrated extended-thinking APIs for multi-step reasoning in production assistant workflows.',
      brief: 'Shipped a multi-step reasoning path from architecture to production and improved deep-query handling.',
      problem: 'Needed more reliable multi-step reasoning in production assistant flows.',
      action: 'Integrated an extended-thinking API path and updated orchestration for step-wise reasoning.',
      result: 'Enabled deeper reasoning traces for complex user queries in production.',
      note: 'Jan 2026-present · AI Engineer @ Made For Planet',
      tag: 'AI'
    },
    {
      num: '02',
      role: 'Frontend Systems',
      summary: 'Reduced frontend request waste across fast search and filter interaction loops.',
      brief: 'Fixed redundant call patterns and tightened UI response under rapid typing.',
      problem: 'Search and filter interactions triggered redundant requests under rapid input.',
      action: 'Added debounce, request guards, and tighter client-side state transitions.',
      result: 'Lowered duplicate API traffic and stabilized search/filter behavior.',
      note: 'Frontend performance and stability improvements',
      tag: 'Frontend'
    },
    {
      num: '03',
      role: 'Backend Systems',
      summary: 'Redesigned core lookup flows to simplify query branching and improve retrieval clarity.',
      brief: 'Reworked username/ID retrieval logic around cleaner data-access patterns.',
      problem: 'Core username and ID lookups had unnecessary query branching.',
      action: 'Redesigned retrieval paths and simplified query structure around access patterns.',
      result: 'Improved lookup clarity and reduced query complexity in critical routes.',
      note: 'Lower query complexity in core lookup routes',
      tag: 'Backend'
    },
    {
      num: '04',
      role: 'Market Consultant @ Livo',
      summary: 'Built a go-to-market strategy framework from research to channel prioritization.',
      brief: 'Created a practical GTM baseline to guide early market-entry decisions.',
      problem: 'GTM decisions lacked a clear prioritization framework.',
      action: 'Built a structured GTM framework with channel and segment prioritization logic.',
      result: 'Created an actionable planning baseline for market-entry decisions.',
      note: 'Aug–Dec 2025 · Market Consultant',
      tag: 'GTM'
    },
    {
      num: '05',
      role: 'Consultant & Team Lead @ 180 Degrees',
      summary: 'Led consulting workstreams across product strategy, AI assessments, and retention diagnostics.',
      brief: 'Drove delivery cadence and cross-team accountability in multi-client engagements.',
      problem: 'Teams needed tighter execution across client consulting workstreams.',
      action: 'Led workstream planning, delegation, and delivery reviews across engagements.',
      result: 'Improved project cadence and accountability across student teams.',
      note: 'Aug 2025–present · Consultant & Team Lead',
      tag: 'Strategy'
    }
  ]
});

const revealedSteps = reactive<Record<number, number>>({ 0: 3 });
const hoveredIndex = ref<number | null>(null);

function visibleSteps(index: number): number {
  return revealedSteps[index] ?? 0;
}

function advance(index: number) {
  const current = revealedSteps[index] ?? 0;
  if (current >= 3) {
    revealedSteps[index] = 0;
  } else {
    revealedSteps[index] = current + 1;
  }
}
</script>

<style scoped>
.exp-list {
  list-style: none;
}

.exp-item {
  display: grid;
  grid-template-columns: 32px 1fr auto;
  gap: 16px;
  padding: 15px 0;
  border-bottom: 1px solid var(--border);
  align-items: start;
  transition: padding-left 0.2s, background 0.2s;
  cursor: pointer;
}

.exp-item:last-child { border-bottom: none; }
.exp-item:hover {
  padding-left: 10px;
  background: rgba(16, 19, 18, 0.035);
}

.exp-num {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.6rem;
  color: var(--muted);
}

.exp-item:hover .exp-num { color: var(--accent); }
.exp-item.is-open .exp-num { color: var(--accent); }

.exp-content {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.exp-role {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  letter-spacing: 0.06em;
  text-transform: uppercase;
  color: #2d3735;
}

.exp-summary {
  font-size: 1rem;
  font-weight: 600;
  line-height: 1.35;
}

.exp-brief {
  max-height: 0;
  opacity: 0;
  overflow: hidden;
  transition: max-height 0.25s ease, opacity 0.2s ease;
}

.exp-brief.is-visible {
  max-height: 56px;
  opacity: 1;
}

.exp-brief p {
  font-size: 0.78rem;
  line-height: 1.45;
  color: var(--muted);
  font-style: italic;
}

.par {
  max-height: 0;
  opacity: 0;
  overflow: hidden;
  transition: max-height 0.3s ease, opacity 0.25s ease, margin-top 0.3s ease;
  margin-top: 0;
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.par.is-visible {
  max-height: 280px;
  opacity: 1;
  margin-top: 6px;
}

.exp-text {
  font-size: 0.91rem;
  font-weight: 500;
  line-height: 1.5;
  max-height: 0;
  opacity: 0;
  overflow: hidden;
  transition: max-height 0.25s ease, opacity 0.2s ease, padding 0.25s ease;
  padding: 0;
  display: block;
}

.exp-text.is-revealed {
  max-height: 120px;
  opacity: 1;
  padding: 4px 0;
}

.exp-text strong {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.66rem;
  color: var(--accent);
  margin-right: 6px;
  display: inline-block;
  min-width: 14px;
}

.exp-note {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  color: #3d4644;
  margin-top: 3px;
}

.exp-hint {
  display: block;
  margin-top: 4px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.58rem;
  color: #5a6462;
  letter-spacing: 0.05em;
}

.exp-hint.done {
  color: var(--accent);
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
