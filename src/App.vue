<template>
  <main class="app">
    <h1>Vue Task Manager</h1>
<AddTask @add-task="handleAddTask"/>
    <div id="app-root">
      
    </div>
  </main>
</template>

<script setup>

import AddTask from './components/AddTask.vue';

function handleAddTask(text){
  console.log(" Task Added:",text);
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
