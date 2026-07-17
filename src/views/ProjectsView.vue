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
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/projects">Projects</RouterLink>
      <RouterLink to="/contact">Contact</RouterLink>
    </nav>
  </header>

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
  --nav-color: #00bcd4;
  --nav-hover: #4b8bff;
  --nav-bg: rgba(15, 15, 20, 0.8);
  --nav-glow: 0 0 8px rgba(0, 188, 212, 0.7);
}

header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--nav-bg);
  backdrop-filter: blur(8px);
  padding: 10px 0;
}

nav {
  display: flex;
  justify-content: center;
  gap: 20px;
  font-family: 'Orbitron', 'Poppins', sans-serif;
  font-size: 16px;
}

nav a {
  text-decoration: none;
  color: var(--nav-color);
  padding: 6px 15px;
  border-radius: 8px;
  border: 1px solid var(--nav-color);
  position: relative;
  transition: all 0.3s ease;
  text-shadow: 0 0 4px rgba(0, 188, 212, 0.5);
}

nav a::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: 0;
  height: 3px;
  width: 100%;
  background: linear-gradient(90deg, #00bcd4, #4b8bff, #00bcd4);
  border-radius: 2px;
  transform: scaleX(0);
  transition: transform 0.3s ease;
}

nav a:hover {
  color: honeydew;
  border-color: var(--nav-hover);
  text-shadow: 0 0 12px rgba(75, 139, 255, 0.8);
}

nav a:hover::after {
  transform: scaleX(1);
}
</style>
