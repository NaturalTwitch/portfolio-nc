<script setup>
import { RouterLink, RouterView } from 'vue-router'
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

  <RouterView />
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
