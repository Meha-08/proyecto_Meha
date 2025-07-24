<script setup>
import { ref } from 'vue';
import EntradaDatos from './EntradaDatos.vue';

const emit = defineEmits(['nuevoUsuario']);

const nombre = ref('');
const correo = ref('');
const telefono = ref('');
const error = ref('');

const enviarFormulario = () => {
  if (!nombre.value || !correo.value || !telefono.value) {
    error.value = 'Todos los campos son obligatorios';
  } else {
    error.value = '';
    emit('nuevoUsuario', {
      nombre: nombre.value,
      correo: correo.value,
      telefono: telefono.value
    });
    nombre.value = '';
    correo.value = '';
    telefono.value = '';
  }
};
</script>

<template>
  <div class="form-container">
    <form @submit.prevent="enviarFormulario" class="formulario">
      <h2>Registro de Usuario</h2>
      <EntradaDatos label="Nombre" v-model="nombre" type="text" placeholder="Ingrese su nombre" />
      <EntradaDatos label="Correo" v-model="correo" type="email" placeholder="Ingrese su correo" />
      <EntradaDatos label="Teléfono" v-model="telefono" type="text" placeholder="Ingrese su teléfono" />
      <p v-if="error" class="error">{{ error }}</p>
      <div class="botones">
        <button type="submit" class="btn guardar">Guardar</button>
        <button type="reset" class="btn eliminar">Eliminar</button>
      </div>
    </form>
  </div>
</template>

<style scoped>
.form-container {
  background: linear-gradient(to bottom right, #43d183, #7af3e5);
  padding: 2em;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
  max-width: 450px;
  margin: auto;
  margin-top: 2em;
}

.formulario {
  display: flex;
  flex-direction: column;
  gap: 1em;
}

h2 {
  text-align: center;
  color: #333;
  margin-bottom: 0.5em;
}

.error {
  color: red;
  font-weight: bold;
  text-align: center;
}

.botones {
  display: flex;
  justify-content: space-between;
  gap: 1em;
}

.btn {
  flex: 1;
  padding: 0.75em;
  border: none;
  border-radius: 6px;
  font-size: 1em;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.guardar {
  background: linear-gradient(120deg, #0c5c44 0%, #6fe95d 100%);
  color: white;
}

.guardar:hover {
  background-color: #388e3c;
}

.eliminar {
  background: linear-gradient(120deg, #db6030 0%, #dbd256 100%);
  color: white;
}

.eliminar:hover {
  background-color: #d32f2f;
}
</style>
