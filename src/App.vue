<template>
  <main class="app">
    <h1>Vue Task Manager</h1>
<AddTask @add-task="handleAddTask"/>
<div class="filters">
  <button 
    :class="{ active: filter === 'all' }"
    @click="filter = 'all'"
  >
    All
  </button>

  <button 
    :class="{ active: filter === 'completed' }"
    @click="filter = 'completed'"
  >
    Completed
  </button>

  <button 
    :class="{ active: filter === 'pending' }"
    @click="filter = 'pending'"
  >
    Pending
  </button>
</div>
<div class="task-list">
 <TaskItem
      v-for="t in filteredTasks"
      :key="t.id"
      :task="t"
      @toggle-task="toggleTask(t.id)"
      @delete-task="deleteTask(t.id)"
    />
    </div>
    <div id="app-root">
      
    </div>
  </main>
</template>

<script setup>

import AddTask from './components/AddTask.vue';
import TaskItem from './components/TaskItem.vue';
import {computed,ref} from 'vue';

const filter = ref("all");

const filteredTasks = computed(() => {
  if (filter.value === "completed") {
    return tasks.value.filter(t => t.completed);
  }
  if (filter.value === "pending") {
    return tasks.value.filter(t => !t.completed);
  }
  return tasks.value;
});


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

.filters {
  display: flex;
  gap: 12px;
  margin: 20px 0;
}

.filters button {
  padding: 8px 16px;
  background: #333;
  color: #eee;
  border: none;
  border-radius: 20px;
  cursor: pointer;
  transition: 0.2s;
  font-size: 14px;
}

.filters button:hover {
  background: #444;
}

.filters button.active {
  background: #42b983;
  color: #fff;
}

body {
  margin: 0;
  background: #111;
  color: #eee;
  font-family: system-ui, sans-serif;
}
.task-list {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.app {
  
  max-width: 700px;
  margin: 40px auto;
  padding: 0 20px;
  background: #1a1a1a;
  border-radius: 8px;
  box-shadow: 0 0 20px rgba(0,0,0,0.4);

}

.filters {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.filters button {
  padding: 6px 14px;
  background: #333;
  color: #eee;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.filters button.active {
  background: #42b983;
  color: #fff;
}

</style>
