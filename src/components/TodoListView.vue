<script setup lang="ts">
import type { Task } from '../types/task';

const props = defineProps<{
  todos: Task[];
  onDelete: (id: number) => void;
}>();
</script>

<template>
  <ul>
    <li v-for="todo in props.todos" :key="todo.id">
      {{ todo.text }}
      <button @click="props.onDelete(todo.id)">Delete</button>
    </li>
  </ul>
</template>
