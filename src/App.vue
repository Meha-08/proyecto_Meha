<script setup>
import { ref } from 'vue'
import Formulario from './components/Formulario.vue'
import Lista from './components/Lista.vue'

const usuarios = ref([])

const agregarUsuario = (usuario) => {
  usuarios.value.push(usuario)
}

const eliminarUsuario = (index) => {
  usuarios.value.splice(index, 1)
}
</script>

<template>
  <div class="layout">
    <aside class="sidebar">
      <div class="sidebar-logo">Mi Empresa</div>
      <ul class="sidebar-links">
        <li><a href="#">Inicio</a></li>
        <li><a href="#">Clientes</a></li>
        <li><a href="#">Contacto</a></li>
      </ul>
    </aside>

    <main class="content">
      <div class="card">
        <h1>Registro de Usuarios</h1>
        <Formulario @nuevoUsuario="agregarUsuario" />
        <Lista :usuarios="usuarios" @eliminar-usuario="eliminarUsuario" />
      </div>
    </main>
  </div>
</template>

<style scoped>
.layout {
  display: flex;
  min-height: 100vh;
}

.sidebar {
  width: 320px;
  background: linear-gradient(135deg, #43e97b, #38f9d7);
  padding: 2rem 1rem;
  border-right: 2px solid #bbdefb;
}

.sidebar-logo {
  font-size: 1.8rem;
  font-weight: bold;
  text-align: center;
  margin-bottom: 2rem;
  color: #ffffff;
}

.sidebar-links {
  list-style: none;
  padding: 0;
}

.sidebar-links li a {
  display: block;
  background: #8efaf8;
  padding: 1rem;
  margin-bottom: 1rem;
  border-radius: 10px;
  text-decoration: none;
  color: #0d47a1;
  text-align: center;
  font-weight: 400;
  transition: background 0.3s ease;
}

.sidebar-links li a:hover {
  background: #a4f2dc;
}

.content {
  flex: 1;
  background: linear-gradient(135deg, #256139, #38f9d7);
  padding: 4rem 2rem;
  display: flex;
   width: 10%;
  justify-content: center;
  align-items: flex-start;
}
  
.card {
  background: linear-gradient(135deg, #256139, #38f9d7);
  padding: 1.2rem;
  border-radius: 20px;
  width: 50%;
  max-width: 650px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}
  
h1 {
  text-align: center;
  color: #bbfadd;
  font-size: 2rem;
  margin-bottom: 2rem;
}
</style>


<style>
body {
  background: linear-gradient(to right, #4ffe52, #00f2fe);
  font-family: 'Segoe UI', Arial, sans-serif;
  margin: 0;
  padding: 0;
  min-height: 100vh;
  color: #222;
}

label {
  font-weight: 500;
  margin-bottom: 4px;
}

input[type="text"],
input[type="email"] {
  padding: 8px 12px;
  border: 1px solid #d0d7de;
  border-radius: 6px;
  font-size: 1rem;
  background: #f9fafb;
  transition: border 0.2s;
  color: #222;
}

input:focus {
  border: 1.5px solid #42b983;
  outline: none;
}

button[type="submit"] {
  background: #42b983;
  color: #fff;
  border: none;
  border-radius: 6px;
  padding: 10px 0;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}

button[type="submit"]:hover {
  background: #369870;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  background: #f3f6fa;
  margin-bottom: 10px;
  padding: 10px 14px;
  border-radius: 6px;
  border: 1px solid #e3e8ee;
  font-size: 1rem;
}

p {
  margin: 0;
}

.error {
  color: #e74c3c;
  background: #fdecea;
  border: 1px solid #f5c6cb;
  border-radius: 4px;
  padding: 6px 10px;
  margin-bottom: 8px;
  font-size: 0.97rem;
}
</style>
