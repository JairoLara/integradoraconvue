<template>
    <div id="app">
      <NavBar />
      
    </div>
  </template>
  
  <script>
  import NavBar from './components/NavBar.vue';
  
  
  export default {
    name: 'App',
    components: {
      NavBar
    }
  }
  </script>
  
  <style>
  body {
    margin: 0;
    padding: 0;
    overflow-x: hidden;
  }
  </style>