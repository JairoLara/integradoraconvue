<template>
    <div>
      <input type="text" v-model="query" placeholder="Buscar" />
      <button @click="search">Buscar</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SearchBar',
    data() {
      return {
        query: ''
      };
    },
    methods: {
      search() {
        this.$emit('search', this.query);
      }
    }
  };
  </script>
  
  <style scoped>
  /* Estilos para la barra de búsqueda */
  </style>