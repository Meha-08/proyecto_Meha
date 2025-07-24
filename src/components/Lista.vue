<script setup>
const props = defineProps(['usuarios']);
const emit = defineEmits(['eliminar-usuario']);

const eliminarusuario = (index) => {
  emit('eliminar-usuario', index);
};
</script>

<template>
  <h2>Lista Usuarios</h2>
  <table>
    <thead>
      <tr>
        <th>Cliente</th>
        <th>Correo</th>
        <th>Teléfono</th>
        <th>Acciones</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(usuario, index) in usuarios" :key="index">
        <td>{{ usuario.nombre }}</td>
        <td>{{ usuario.correo }}</td>
        <td>{{ usuario.telefono }}</td>
        <td><button @click="eliminarusuario(index)" class="btn-eliminar">Eliminar</button></td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
h2 {
  text-align: center;
  color: #333;
  margin-top: 1em;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 1em;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  overflow: hidden;
}

th {
  background: linear-gradient(to right, #4facfe, #00f2fe);
  color: white;
  padding: 1em;
  text-align: left;
  font-weight: bold;
}

td {
  padding: 0.75em 1em;
  border-bottom: 1px solid #ddd;
}

tbody tr:nth-child(odd) {
  background-color: #f9f9f9;
}

tbody tr:nth-child(even) {
  background-color: #eef6fb;
}

tbody tr:hover {
  background-color: #d0ebff;
  cursor: pointer;
}

.btn-eliminar {
  background-color: #ff4d4f;
  color: white;
  border: none;
  padding: 0.4em 0.8em;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn-eliminar:hover {
  background-color: #d9363e;
}
</style>
