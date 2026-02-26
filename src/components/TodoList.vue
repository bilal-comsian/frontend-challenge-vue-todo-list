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
         
  } catch (e) {
    apiTodos.value = [];
  }
};


onMounted(() => {
  fetchApiTodos();
});
const newTodo = ref('');
const newApiTodo = ref('');

const addTask = async () => {
  const trimmed = newTodo.value.trim();
  if (!trimmed) return;
  todos.value.push({ id: Date.now(), text: trimmed });
  newTodo.value = '';
};
const deleteTask = async (id: number) => {
  todos.value = todos.value.filter(todo => todo.id !== id);
};
// API Add Task
const addApiTask = async () => {
  const trimmed = newApiTodo.value.trim();
  if (!trimmed) return;
  try {
    const res = await fetch('https://retoolapi.dev/xaoo5W/tasks', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ name: trimmed }),
    });
    if (!res.ok) throw new Error('Failed to add task');
    await fetchApiTodos();
    newApiTodo.value = '';
  } catch (e) {
    // Optionally handle error
  }
};

// API Delete Task
const deleteApiTask = async (id: number) => {
  try {
    const res = await fetch(`https://retoolapi.dev/xaoo5W/tasks/${id}`, {
      method: 'DELETE',
    });
    if (!res.ok) throw new Error('Failed to delete task');
    await fetchApiTodos();
  } catch (e) {
    // Optionally handle error
  }
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
  

  <div style="margin-top:2rem">
    <h2>API Tasks</h2>
    <div>
      <input v-model="newApiTodo" type="text" placeholder="New API task" />
      <button @click="addApiTask">Add API Task</button>
    </div>
    <ul>
      <li v-for="task in apiTodos" :key="task.id">
        <span>ID: {{ task.id }}</span>
        <span style="margin-left: 1em;">
          Name: {{ task.name }}
        </span>
        <button style="margin-left: 1em;" @click="deleteApiTask(task.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>
    