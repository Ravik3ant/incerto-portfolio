<template>
  <header class="hero section-inner">
    <div class="section-label">§ Intro</div>
    <div class="section-body hero-inner">
      <span class="hero-tag">Incerto · Intern</span>

      <h1 class="hero-title">
        Hey, I'm <em>Ravikant.</em><br>
        I build and analyze physical systems at small scales.<br>
        Focused on extracting simple models from messy reality.<br>
      </h1>

      <p class="hero-sub">
        I connect first-principles modeling, production AI engineering, and product execution.<br>
        Sophomore at BITS Hyderabad (M.Sc. Physics + B.E. EEE), focused on term project.
      </p>

      <div class="hero-links">
        <a href="mailto:ravik3ant@gmail.com" class="hero-link">ravik3ant@gmail.com</a>
        <a href="https://github.com/Ravik3ant" target="_blank" class="hero-link">GitHub</a>
        <a href="https://linkedin.com/in/Ravik3ant" target="_blank" class="hero-link">LinkedIn</a>
        <a href="/resume.pdf" target="_blank" class="hero-link">Resume</a>
      </div>
    </div>
  </header>
</template>

<style scoped>
.hero {
  min-height: 72vh;
  position: relative;
  z-index: 1;
  border-bottom: 1px solid var(--border);
}

.hero-inner {
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 72vh;
  max-width: 760px;
}

.hero-tag {
  display: inline-block;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--muted);
  border: 1px solid var(--border);
  padding: 6px 12px;
  margin-bottom: 26px;
  width: fit-content;
}

.hero-title {
  font-size: clamp(2.2rem, 4.4vw, 3.4rem);
  font-weight: 600;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: 18px;
}

.hero-title em {
  font-family: 'Instrument Serif', serif;
  font-style: italic;
  font-weight: 400;
  color: var(--accent);
}

.hero-sub {
  font-size: 0.96rem;
  line-height: 1.75;
  color: var(--muted);
  max-width: 620px;
  margin-bottom: 24px;
}

.hero-links {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
}

.hero-link {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.67rem;
  letter-spacing: 0.07em;
  color: var(--ink);
  padding-bottom: 2px;
  border-bottom: 1px solid var(--ink);
  transition: color 0.2s, border-color 0.2s;
}

.hero-link:hover {
  color: var(--accent);
  border-color: var(--accent);
}

@media (max-width: 768px) {
  .hero,
  .hero-inner {
    min-height: auto;
  }
}
</style>
