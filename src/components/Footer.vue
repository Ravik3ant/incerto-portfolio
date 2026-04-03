<template>
  <footer>
    <span>Ravikant · Built for Incerto · 2026</span>
    <span>Remote</span>
  </footer>
</template>

<style scoped>
footer {
  padding: 16px 48px;
  display: flex;
  justify-content: space-between;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.58rem;
  color: var(--muted);
  letter-spacing: 0.08em;
  border-top: 1px solid var(--border);
  position: relative;
  z-index: 1;
  background: var(--bg);
}

@media (max-width: 768px) {
  footer {
    flex-direction: column;
    gap: 4px;
    padding: 14px 20px;
    text-align: center;
  }
}
</style>
