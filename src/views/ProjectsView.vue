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

<style scoped></style>
