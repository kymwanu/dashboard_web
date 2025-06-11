<template>
  <div class="metric-card" :class="{ 'dark-theme': isDarkTheme }">
    <h3>{{ title }}</h3>
    <p>{{ value }}</p>
    <p class="description">{{ description }}</p>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
  title: {
    type: String,
    required: true,
  },
  value: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    default: '',
  },
  isDarkTheme: {
    type: Boolean,
    default: false,
  },
})
</script>

<style scoped>
.metric-card {
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: var(--card-background);
  color: var(--text-color);
}

.metric-card.dark-theme {
  background-color: var(--dark-card-background);
  color: var(--dark-text-color);
}

.description {
  font-size: 0.9em;
  color: var(--description-color);
}
</style>
