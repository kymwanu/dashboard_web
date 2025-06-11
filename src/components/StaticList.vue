<template>
  <div class="static-list">
    <h3>Static List</h3>
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const items = ref(['Feature 1', 'Feature 2', 'Feature 3', 'Feature 4', 'Feature 5'])
</script>

<style scoped>
.static-list {
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: var(--background-color);
}

.static-list h3 {
  margin-bottom: 10px;
}

.static-list ul {
  list-style-type: none;
  padding: 0;
}

.static-list li {
  margin: 5px 0;
}
</style>
