<template>
  <div id="app" :class="theme">
    <router-view />
  </div>
</template>

<script setup>
import { ref } from 'vue'

const theme = ref('light')
</script>

<style>
@import './assets/styles/variables.css';
@import './assets/styles/themes.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
