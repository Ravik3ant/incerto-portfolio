<template>
  <div class="field-wrap" aria-hidden="true">
    <div class="wash wash-a" />
    <div class="wash wash-b" />
    <div class="texture" />
  </div>
</template>

<style scoped>
.field-wrap {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 0;
}

.wash,
.texture {
  position: absolute;
  inset: 0;
}

.wash-a {
  background:
    radial-gradient(58rem 30rem at 8% 5%, rgba(20, 184, 166, 0.065), transparent 72%),
    radial-gradient(38rem 24rem at 92% 10%, rgba(15, 118, 110, 0.045), transparent 72%);
}

.wash-b {
  background:
    radial-gradient(42rem 26rem at 50% 78%, rgba(13, 148, 136, 0.04), transparent 75%);
}

.texture {
  background-image:
    linear-gradient(to right, rgba(26, 26, 26, 0.012) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(26, 26, 26, 0.012) 1px, transparent 1px);
  background-size: 34px 34px;
  opacity: 0.28;
}
</style>
