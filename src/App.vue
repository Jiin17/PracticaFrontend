<template>
    <h1>Lista de tareas</h1>
    <input v-model="nuevoTexto" placeholder="Nombre de la tarea" @keyup.enter="agregarCheckbox"> <br> <br>
    <button @click="agregarCheckbox">Agregar Checkbox</button>
    <div v-for="(checkbox, index) in checkboxes" :key="index" :class="espacio">
      <input type="checkbox" v-model="checkbox.checked">
      <label>{{ checkbox.text }}</label>
      <button @click="eliminarCheckbox(index)" style="background-color: #3498db ; color: black;">Eliminar</button>
    </div>
</template>

<script>
export default {
  name: 'App',
  data() {
        return {
          nuevoTexto: '',
          checkboxes: []
        };
      },
      methods: {
        agregarCheckbox() {
          if (this.nuevoTexto.trim() !== '') {
            this.checkboxes.push({ text: this.nuevoTexto, checked: false });
            this.nuevoTexto = '';
          }
        },
        eliminarCheckbox(index) {
          this.checkboxes.splice(index, 1);
        }
      }
    };
</script>

<style>
.espacio{
  margin-bottom: 50px;
  padding-left: 100px;
}
</style>
