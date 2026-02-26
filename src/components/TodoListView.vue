
<script setup lang="ts">
import type { Task } from '../types/task';
import '../style/todolist.css';

const props = defineProps<{
  todos: Task[];
  onDelete: (id: number) => void;
}>();
</script>

<template>
  <ul class="todo-list">
    <li v-for="todo in props.todos" :key="todo.id" class="todo-item">
      <span class="todo-text">{{ todo.text }}</span>
      <span
        class="delete-icon"
        @click="props.onDelete(todo.id)"
        title="Delete"
        role="button"
        tabindex="0"
        @keydown.enter="props.onDelete(todo.id)"
        aria-label="Delete task"
      >
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <line x1="5" y1="5" x2="15" y2="15" stroke="#ff4d4f" stroke-width="2" stroke-linecap="round"/>
          <line x1="15" y1="5" x2="5" y2="15" stroke="#ff4d4f" stroke-width="2" stroke-linecap="round"/>
        </svg>
      </span>
    </li>
  </ul>
</template>




