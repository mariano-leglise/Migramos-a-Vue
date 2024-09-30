<template>
  <div class="login-container">
    <form @submit.prevent="login" class="login-form">
      <h1 class="login-title">Login</h1>
      <div class="form-group">
        <label for="username">Nombre:</label>
        <input
          v-model="user.username"
          type="text"
          id="username"
          required
          placeholder="Ingrese su nombre de usuario"
        />
      </div>
      <div class="form-group">
        <label for="password">Contraseña:</label>
        <input
          v-model="user.password"
          type="password"
          id="password"
          required
          placeholder="Ingrese su contraseña"
        />
      </div>
      <button type="submit" class="login-button">Ingresar</button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import { useUserStore } from '../stores/userStore'
import { User } from '../models/User'

const user = ref<User>({ username: '', password: '' })
const router = useRouter()
const userStore = useUserStore()

const login = () => {
  userStore.setUser(user.value)
  router.push('/home')
}
</script>

<style scoped>
/* Degradado de fondo*/
.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(135deg, #5e0404, #0c0b0c); /* Degradado*/
  font-family: 'Roboto', sans-serif;
  margin: 0;
  padding: 0;
}

/* Estilo del formulario */
.login-form {
  background-color: rgba(20, 20, 20, 0.8);
  padding: 2rem;
  border-radius: 12px;
  backdrop-filter: blur(5px); /* Desenfoque del fondo */
  border: none; /* Sin borde */
  box-shadow: 0px 10px 20px rgba(0, 0, 0, 0.7); /* Sombra negra */
  width: 100%;
  max-width: 400px;
  color: white;
  overflow: hidden;
}

/* Título del formulario */
.login-title {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  text-align: center;
  color: #5e0404;
  font-weight: bold;
  text-transform: uppercase;
  letter-spacing: 0.1em;
}

/* Estilo de los campos de entrada */
.form-group {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 600;
  color: #5e0404;
}

input {
  width: 100%;
  padding: 0.75rem;
  border: 2px solid #5e0404; /* Borde fucsia oscuro */
  border-radius: 8px;
  background-color: rgba(255, 255, 255, 0.1); /* Fondo blanco translúcido */
  color: white;
  font-size: 1rem;
  box-sizing: border-box;
  transition: border-color 0.3s ease;
  outline: none;
}

input::placeholder {
  color: rgba(255, 255, 255, 0.6);
}

input:focus {
  border-color: #4c2f8b; /* Cambia a un tono más oscuro de violeta */
  outline: none;
}

/* Estilo del botón */
.login-button {
  width: 100%;
  padding: 0.75rem;
  background-color: #5e0404; /* Color fucsia oscuro */
  color: white;
  font-size: 1.2rem;
  font-weight: bold;
  text-transform: uppercase;
  border: none; /* Sin borde */
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  letter-spacing: 0.05em;
}

.login-button:hover {
  background-color: #4c2f8b; /* Cambia a un tono más oscuro de violeta */
}

/* Ajustes de focus en el botón */
button:focus {
  outline: none;
}
</style>
