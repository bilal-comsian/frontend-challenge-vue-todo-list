<script setup lang="ts">

import { ref, onMounted } from 'vue';
import TodoListView from './TodoListView.vue';

const todos = ref<any[]>([]);
const apiTodos = ref<any[]>([]);
const fetchApiTodos = async () => {
  try {
    const res = await fetch('https://retoolapi.dev/xaoo5W/tasks');
    if (!res.ok) throw new Error('Failed to fetch');
    apiTodos.value = await res.json();
    apiTodos.value.forEach(element => {
      todos.value.push({ id: element.id , text: element.name });
    });
     
  } catch (e) {
    apiTodos.value = [];
  }
};

onMounted(() => {
  fetchApiTodos();
});
const newTodo = ref('');

const addTask = async () => {
  const trimmed = newTodo.value.trim();
  if (!trimmed) return;
  todos.value.push({ id: Date.now(), text: trimmed });
  newTodo.value = '';
};
const deleteTask = async (id: number) => {
  todos.value = todos.value.filter(todo => todo.id !== id);
};
</script>

<template>
  <section>
    <h1>To Do List</h1>

    <div>
      <input v-model="newTodo" type="text" placeholder="New task" />
      <button @click="addTask">Add</button>
    </div>

    <TodoListView :todos="todos" :onDelete="deleteTask" />
  </section>
  

  <!-- <div style="margin-top:2rem">
    <h2>API Tasks</h2>
    <ul>
      <li v-for="task in apiTodos" :key="task.id">
        <span>ID: {{ task.id }}</span>
        <span style="margin-left: 1em;">
          Name: {{ task.name }}
        </span>
      </li>
    </ul>
  </div> -->
</template>
