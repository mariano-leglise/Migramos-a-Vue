<template>
  <div class="home-container">
    <h1 class="welcome-message">¡Bienvenido, {{ user.username }}!</h1>
    <h2 class="campus-title">Campus Virtual</h2>
    <ul class="subject-list">
      <li>Programación Frontend</li>
      <li>Programación Backend</li>
      <li>Desarrollo de Software</li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { useUserStore } from '../stores/userStore'

const userStore = useUserStore()
const user = userStore.user
</script>

<style scoped>
.home-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: linear-gradient(135deg, #5e0404, #0c0b0c); /* Fondo del campus virtual */
  color: white;
  text-align: center;
}

.welcome-message {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.campus-title {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.subject-list {
  list-style-type: none;
  padding: 0;
}

.subject-list li {
  font-size: 1.5rem;
  margin: 0.5rem 0;
  padding: 0.5rem;
  border: 1px solid rgba(255, 255, 255, 0.5);
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.subject-list li:hover {
  background-color: rgba(255, 255, 255, 0.2);
}
</style>
