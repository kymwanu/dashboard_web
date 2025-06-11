<template>
  <div class="theme-toggle">
    <label class="switch">
      <input type="checkbox" v-model="isDarkTheme" @change="toggleTheme" />
      <span class="slider round"></span>
    </label>
    <span>{{ isDarkTheme ? 'Dark Mode' : 'Light Mode' }}</span>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isDarkTheme = ref(false)

const toggleTheme = () => {
  document.body.classList.toggle('dark-theme', isDarkTheme.value)
  localStorage.setItem('theme', isDarkTheme.value ? 'dark' : 'light')
}

// Carrega o tema salvo ao iniciar
onMounted(() => {
  const saved = localStorage.getItem('theme')
  if (saved === 'dark') {
    isDarkTheme.value = true
    document.body.classList.add('dark-theme')
  } else {
    isDarkTheme.value = false
    document.body.classList.remove('dark-theme')
  }
})
</script>

<style scoped>
.theme-toggle {
  display: flex;
  align-items: center;
}
.switch {
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}
.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}
.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  transition: 0.4s;
  border-radius: 34px;
}
.slider:before {
  position: absolute;
  content: '';
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  transition: 0.4s;
  border-radius: 50%;
}
input:checked + .slider {
  background-color: #38e6b0;
}
input:checked + .slider:before {
  transform: translateX(26px);
}
</style>
