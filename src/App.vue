<script setup lang="ts">
import TodoList from './components/TodoList.vue';
</script>

<template>
  <main class="app-container">
    <TodoList />
  </main>
</template>

<style scoped>
.app-container {
  max-width: 960px;
  margin: 0 auto;
  padding: 2rem 1rem;
}
</style>