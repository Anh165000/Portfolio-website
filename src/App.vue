<template>
  <div id="app-container">
    <Portfolio />
  </div>
</template>

<script setup>
import Portfolio from './views/Portfolio.vue'
import './assets/portfolio.css'
</script>

<style>
/* Global Styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  width: 100%;
  height: 100%;
  overflow-x: hidden;
}

#app-container {
  width: 100%;
  min-height: 100vh;
  background-color: var(--dark-bg);
}
</style>
