<script setup>

import profileSrc from '../assets/Me.png';
</script>

<template>
  <main class="landing">
    <div class="stars"></div>
    <div class="landing-inner">
      <div class="text-block">
        <h1 class="intro">Hello, I'm</h1>
        <h1 class="fancyName">Normand Cardinal</h1>
        <p class="subtitle">Full-Stack Developer • Automation Enthusiast • Creator of Mursy</p>
        <ul class="roles">
          <li>💻 Full-Stack Dev</li>
          <li>🤖 Automation & Bots</li>
          <li>🎮 Game Tools & Mods</li>
          <li>🧪 AI & VR Experiments</li>
        </ul>
        <div class="landing-cta">
          <a href="/projects" class="cta">View Projects</a>
          <a href="/contact" class="cta ghost">Contact Me</a>
        </div>
      </div>
      <div class="visual-block">
        <img :src="profileSrc" alt="NaturalTwitch" class="avatar" />
      </div>
    </div>
  </main>
</template>

<style scoped>
:root {
  --neon-primary: #00bcd4;
  --neon-secondary: #4b8bff;
  --glow: 0 0 12px rgba(0, 188, 212, 0.6);
  --text: #e0e0e0;
  --bg: #0d1117;
}

.landing {
  position: relative;
  min-height: 80vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--bg);
  color: var(--text);
  font-family: 'Orbitron', 'Poppins', sans-serif;
  padding: 30px;
  overflow: hidden;
}

.stars {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: transparent;
  z-index: 0;
}

.stars::after {
  content: "";
  position: absolute;
  width: 2px;
  height: 2px;
  background: white;
  box-shadow:
    10vw 20vh white, 30vw 40vh white, 50vw 70vh white, 70vw 10vh white,
    20vw 90vh white, 60vw 50vh white, 80vw 30vh white, 40vw 60vh white,
    15vw 40vh white, 35vw 80vh white, 55vw 20vh white, 75vw 60vh white;
  animation: twinkle 3s infinite alternate;
  border-radius: 50%;
}

@keyframes twinkle {
  0% {
    opacity: 0.2;
  }

  50% {
    opacity: 1;
  }

  100% {
    opacity: 0.2;
  }
}

.landing-inner {
  position: relative;
  display: grid;
  grid-template-columns: 1fr 300px;
  align-items: center;
  gap: 30px;
  z-index: 1;
}

.text-block {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.intro {
  font-size: 1.6rem;
  font-weight: 400;
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
  font-size: 1.1rem;
  opacity: 0.7;
  letter-spacing: 0.5px;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  padding-top: 10px;
}

.roles {
  list-style: none;
  padding: 0;
  margin: 10px 0 0 0;
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  font-weight: 600;
  color: var(--neon-primary);
}

.roles li {
  background: rgba(0, 188, 212, 0.06);
  border: 1px solid rgba(0, 188, 212, 0.12);
  padding: 6px 12px;
  border-radius: 999px;
  font-size: 0.95rem;
}

.landing-cta {
  margin-top: 18px;
  display: flex;
  gap: 12px;
}

.cta {
  padding: 8px 14px;
  background: linear-gradient(90deg, var(--neon-primary), var(--neon-secondary));
  color: var(--text);
  border-radius: 8px;
  font-weight: 700;
  text-decoration: none;
  box-shadow: 0 6px 20px rgba(0, 188, 212, 0.12);
  display: inline-block;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.cta:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 28px rgba(0, 188, 212, 0.2);
}

.cta.ghost {
  background: transparent;
  border: 1px solid rgba(0, 188, 212, 0.12);
  color: var(--text);
}

.visual-block .avatar {
  width: 280px;
  border-radius: 300px;
  border: 0px solid rgba(0, 188, 212, 0.12);
  box-shadow: 0 0 20px rgba(0, 188, 212, 0.06);
}

@media (max-width: 820px) {
  .landing-inner {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .visual-block {
    margin-top: 20px;
  }

  .fancyName {
    font-size: 2.6rem;
  }

  .roles li {
    font-size: 0.85rem;
  }

  .landing-cta {
    justify-content: center;
  }
}

@media (max-width: 420px) {
  .fancyName {
    font-size: 2.2rem;
    letter-spacing: 0.5px;
  }

  .intro {
    font-size: 1.2rem;
  }

  .subtitle {
    font-size: 0.9rem;
  }
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

  50% {
    background-position: 100% 50%;
  }

  100% {
    background-position: 0% 50%;
  }
}

@media (prefers-reduced-motion: reduce) {
  .fancyName {
    animation: none !important;
    transition: none !important;
  }
}
</style>
