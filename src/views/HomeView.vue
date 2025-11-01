<script setup>

</script>

<template>
  <main class="introContainer">
    <h1 class="intro">Hello, I'm</h1>
    <h1 class="fancyName">NaturalTwitch</h1>
    <p class="subtitle">Full-Stack Developer • Automation Enthusiast • Creator of Mursy</p>
  </main>
</template>

<style scoped>
:root {
  --glow: 0 0 10px rgba(0, 200, 255, 0.8);
  --accent: #00bcd4;
  --text: #e0e0e0;
}

.introContainer {
  min-height: 50vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  background: radial-gradient(circle at 20% 20%, #0d1117 0%, #000 100%);
  color: var(--text);
  font-family: 'Orbitron', 'Poppins', sans-serif;
  letter-spacing: 1px;
  padding: 20px;
}

.intro {
  font-weight: 400;
  font-size: 1.8rem;
  margin: 0;
  opacity: 0.8;
}

.fancyName {
  font-size: 3.8rem;
  font-weight: 700;
  background: linear-gradient(90deg, #00bcd4, #4b8bff, #00bcd4);
  background-size: 600% 600%;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  color: transparent;

  text-shadow: var(--glow);
  animation: flow 5s linear infinite, pulse 3s infinite alternate;

  display: inline-block;
  line-height: 1;
  margin: 8px 0;
}

.subtitle {
  margin-top: 10px;
  font-size: 1.1rem;
  opacity: 0.7;
  letter-spacing: 0.5px;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding-top: 10px;
}

@keyframes pulse {
  0% {
    text-shadow: 0 0 5px rgba(0, 200, 255, 0.6);
  }

  100% {
    text-shadow: 0 0 20px rgba(75, 139, 255, 0.9);
  }
}

@keyframes flow {
  0% {
    background-position: 0% 50%;
  }

  100% {
    background-position: 100% 50%;
  }
}


@media (max-width: 760px) {
  .introContainer {
    min-height: 38vh;
    padding: 18px;
    justify-content: center;
  }

  .intro {
    font-size: 1.2rem;
  }

  .fancyName {
    font-size: 2.2rem;
    margin: 6px 0;
    text-shadow: 0 0 2px rgba(0, 200, 255, 0.25);
    animation: flow 6s linear infinite;
    background-image: none;
    -webkit-background-clip: initial;
    background-clip: initial;
    -webkit-text-fill-color: initial;
    color: var(--accent);
  }

  .subtitle {
    font-size: 0.95rem;
    padding-top: 8px;
    border-top: 1px solid rgba(255, 255, 255, 0.06);
  }
}


@media (max-width: 420px) {
  .fancyName {
    font-size: 1.8rem;
    letter-spacing: 0.5px;
  }

  .intro {
    font-size: 1.05rem;
  }

  .subtitle {
    font-size: 0.9rem;
  }
}


@media (prefers-reduced-motion: reduce) {

  .fancyName,
  .projects-title,
  .repo-name {
    animation: none !important;
    transition: none !important;
  }
}
</style>
