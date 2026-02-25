<script setup lang="ts">
// import { defineProps } from 'vue';

type Todo = {
  id: number;
  text: string;
};

const props = defineProps<{
  todos: Todo[];
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
