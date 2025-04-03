<template>
  <div class="app">
    <h1>Gestor de Nombres</h1>
    <div>
      <input v-model="newName" placeholder="Escribe un nombre" />
      <button @click="addName">Agregar</button>
    </div>
    <ul>
      <li v-for="(name, index) in names" :key="index">
        <input type="radio" :value="index" v-model="selectedIndex" />
        {{ name }}
      </li>
    </ul>
    <button @click="removeName" :disabled="selectedIndex === null">Eliminar Seleccionado</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newName: "",
      names: [],
      selectedIndex: null,
    };
  },
  methods: {
    addName() {
      if (this.newName.trim()) {
        this.names.push(this.newName.trim());
        this.newName = ""; // Limpiar el input
      }
    },
    removeName() {
      if (this.selectedIndex !== null) {
        this.names.splice(this.selectedIndex, 1);
        this.selectedIndex = null; // Reiniciar selección
      }
    },
  },
};
</script>

<style scoped>
.app {
  font-family: Arial, sans-serif;
  padding: 20px;
}
input {
  margin-right: 10px;
}
button {
  margin-top: 10px;
}
ul {
  list-style-type: none;
  padding: 3;
}
li {
  margin: 5px 0;
}
</style>
