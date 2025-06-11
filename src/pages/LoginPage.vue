<template>
  <div class="login-view">
    <LoginPanel />
  </div>
</template>

<script setup>
import LoginPanel from '../components/LoginPanel.vue'
</script>

<style scoped>
.login-view {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: var(--background-color);
}
</style>
