<template>
  <div class="parked-page">
    <div class="card">
      <div class="icon">🚀</div>
      <h1>Domain Parked</h1>
      <p>
        This domain is currently reserved and waiting for its next adventure.
      </p>

      <div class="divider"></div>

      <small>
        © {{ new Date().getFullYear() }} All rights reserved.
      </small>
    </div>
  </div>
</template>

<style scoped>
.parked-page {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(135deg, #0f172a, #1e293b);
  font-family: Inter, Arial, sans-serif;
  color: white;
}

.card {
  text-align: center;
  padding: 3rem;
  max-width: 500px;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(12px);
  box-shadow: 0 20px 50px rgba(0, 0, 0, .3);
}

.icon {
  font-size: 4rem;
  margin-bottom: 1rem;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

p {
  color: #cbd5e1;
  font-size: 1.1rem;
  line-height: 1.6;
}

.divider {
  height: 1px;
  background: rgba(255, 255, 255, .2);
  margin: 2rem 0;
}

small {
  color: #94a3b8;
}
</style>
