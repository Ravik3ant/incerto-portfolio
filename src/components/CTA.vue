<template>
  <section class="cta-section">
    <div class="cta-inner">
      <div class="cta-main">
        <p class="cta-text">{{ text }}</p>
        <div class="cta-links">
          <a href="mailto:ravik3ant@gmail.com">ravik3ant@gmail.com</a>
          <span>·</span>
          <a href="tel:+918488911420">+91 84889 11420</a>
        </div>
      </div>

      <a class="resume-preview" href="/resume.pdf" target="_blank" rel="noopener noreferrer" aria-label="Open resume PDF">
        <div class="resume-paper">
          <div class="paper-head">
            <span>Ravikant Patil</span>
            <span>Resume</span>
          </div>
          <div class="paper-line" />
          <div class="paper-line short" />
          <div class="paper-line" />
          <div class="paper-line short" />
          <div class="paper-block" />
          <div class="paper-line" />
          <div class="paper-line short" />
          <div class="paper-line" />
        </div>
        <span class="resume-caption">Open resume →</span>
      </a>
    </div>
  </section>
</template>

<script setup lang="ts">
withDefaults(defineProps<{
  text?: string;
}>(), {
  text: 'If you want someone who thinks deeply about hard problems, let\'s talk.'
});
</script>

<style scoped>
.cta-section {
  background: var(--ink);
  color: var(--bg);
  padding: 64px 48px;
  position: relative;
  z-index: 1;
}

.cta-inner {
  max-width: 1120px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 40px;
  align-items: start;
}

.cta-main {
  max-width: 620px;
}

.cta-text {
  font-size: 1.3rem;
  font-weight: 500;
  line-height: 1.5;
  margin-bottom: 24px;
}

.cta-links {
  display: flex;
  gap: 12px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.72rem;
  letter-spacing: 0.05em;
}

.cta-links a {
  border-bottom: 1px solid var(--bg);
  padding-bottom: 2px;
  transition: opacity 0.2s;
}

.cta-links a:hover { opacity: 0.7; }

.cta-links span { color: var(--accent-light); }

.resume-preview {
  display: inline-flex;
  flex-direction: column;
  gap: 10px;
  color: var(--bg);
  align-items: flex-start;
  justify-self: end;
  margin-top: 4px;
}

.resume-paper {
  width: 150px;
  aspect-ratio: 1 / 1.414;
  background: #f9f8f5;
  color: #1a1a1a;
  border: 1px solid rgba(255, 255, 255, 0.2);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.22);
  padding: 10px;
  display: grid;
  grid-auto-rows: min-content;
  gap: 6px;
  transition: transform 0.22s ease, box-shadow 0.22s ease;
}

.resume-preview:hover .resume-paper {
  transform: translateY(-3px);
  box-shadow: 0 16px 28px rgba(0, 0, 0, 0.28);
}

.paper-head {
  display: flex;
  justify-content: space-between;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.36rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

.paper-line {
  height: 1.5px;
  background: #202020;
  opacity: 0.45;
}

.paper-line.short {
  width: 74%;
}

.paper-block {
  height: 20px;
  border: 1px solid rgba(32, 32, 32, 0.3);
  background: repeating-linear-gradient(
    -45deg,
    rgba(32, 32, 32, 0.08),
    rgba(32, 32, 32, 0.08) 4px,
    transparent 4px,
    transparent 8px
  );
}

.resume-caption {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  opacity: 0.9;
  text-align: left;
}

@media (max-width: 768px) {
  .cta-section { padding: 48px 20px; }
  .cta-inner {
    grid-template-columns: 1fr;
    gap: 22px;
  }
  .cta-main {
    max-width: none;
  }
  .resume-preview {
    justify-self: start;
    margin-top: 8px;
  }
  .cta-links { flex-wrap: wrap; }
}
</style>
