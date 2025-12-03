<template>
  <main class="app">
    <h1>Vue Task Manager</h1>
<AddTask @add-task="handleAddTask"/>

 <TaskItem
      v-for="t in tasks"
      :key="t.id"
      :task="t"
      @toggle-task="toggleTask(t.id)"
      @delete-task="deleteTask(t.id)"
    />
    <div id="app-root">
      
    </div>
  </main>
</template>

<script setup>

import AddTask from './components/AddTask.vue';
import TaskItem from './components/TaskItem.vue';
import {ref} from 'vue';

const tasks=ref([]);
function handleAddTask(text){
   tasks.value.push({
    id: Date.now(),
    text,
    completed: false
  });
}

function toggleTask(id) {
  const t = tasks.value.find(t => t.id === id);
  if (t) t.completed = !t.completed;
}

function deleteTask(id) {
  tasks.value = tasks.value.filter(t => t.id !== id);
}
</script>

<style>
body {
  margin: 0;
  background: #111;
  color: #eee;
  font-family: system-ui, sans-serif;
}
.app {
  max-width: 700px;
  margin: 40px auto;
  padding: 0 20px;
}
</style>
