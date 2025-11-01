<script setup>
import { ref, onMounted } from 'vue'

const repos = ref([])

onMounted(async () => {
  const response = await fetch('https://api.github.com/users/NaturalTwitch/repos')
  const data = await response.json()
  repos.value = data
})
</script>

<template>
  <section class="projects">
    <h2 class="projects-title">My GitHub Projects</h2>
    <div class="repo-grid">
      <div v-for="repo in repos" :key="repo.id" class="repo-card">
        <a :href="repo.html_url" target="_blank">
          <h3 class="repo-name" :data-text="repo.name">{{ repo.name }}</h3>
          <p class="repo-desc">{{ repo.description || 'No description provided.' }}</p>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
:root {
  --neon-primary: #00bcd4;
  --neon-secondary: #4b8bff;
  --bg-card: rgba(15, 15, 20, 0.8);
}


.projects {
  padding: 40px 20px;
  font-family: 'Orbitron', 'Poppins', sans-serif;
  color: #e0e0e0;
  text-align: center;
}

.projects-title {
  font-size: 2.8rem;
  font-weight: 700;
  background: linear-gradient(90deg, #00bcd4, #4b8bff, #00bcd4);
  background-size: 600% 600%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: var(--glow);
  animation: flow 5s linear infinite, pulse 3s infinite alternate;
}

.repo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
}


.repo-card {
  background: var(--bg-card);
  border: 1px solid var(--neon-primary);
  border-radius: 12px;
  padding: 20px;
  text-align: left;
  transition: transform 0.3s, box-shadow 0.3s;
  box-shadow: 0 0 10px rgba(0, 188, 212, 0.3);
}

.repo-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 0 25px rgba(75, 139, 255, 0.8), 0 0 50px rgba(0, 188, 212, 0.6);
}

.repo-card a {
  text-decoration: none;
  color: #e0e0e0;
}


.repo-name {
  font-size: 1.3rem;
  margin-bottom: 10px;
  color: #00e1ffc4;
  background: linear-gradient(270deg, var(--neon-primary), var(--neon-secondary), var(--neon-primary));
  background-size: 600% 600%;
  position: relative;
  z-index: 1;
  -webkit-background-clip: text;
  animation: flow 5s linear infinite, pulse 3s infinite alternate;
}

.repo-name::before {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;
  color: var(--neon-primary);
  opacity: 0.5;
}

.repo-desc {
  font-size: 0.95rem;
  opacity: 0.7;
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

@keyframes pulse {
  0% {
    text-shadow: 0 0 5px rgba(0, 200, 255, 0.6);
  }

  100% {
    text-shadow: 0 0 20px rgba(75, 139, 255, 0.9);
  }
}

@media (max-width: 760px) {

  .projects {
    padding: 22px 12px;
  }

  .projects-title {
    font-size: 1.6rem;
    margin-bottom: 18px;
    background-image: none;
    background-size: initial;
    -webkit-background-clip: initial;
    background-clip: initial;
    -webkit-text-fill-color: initial;
    color: var(--neon-primary);
    animation: none;
    display: inline-block;
  }

  .repo-grid {
    grid-template-columns: 1fr;
    gap: 12px;
  }

  .repo-card {
    padding: 12px;
    min-height: auto;
  }

  .repo-link {
    padding: 14px;
  }

  .repo-name {
    font-size: 1.05rem;
    background-image: none;
    -webkit-background-clip: initial;
    background-clip: initial;
    -webkit-text-fill-color: initial;
    color: var(--neon-primary);
    animation: none;
    display: inline-block;
    word-break: break-word;
  }

  .repo-desc {
    -webkit-line-clamp: 4;
    font-size: 0.94rem;
  }
}
</style>
