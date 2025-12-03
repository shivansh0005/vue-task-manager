<!-- <script setup>
import { ref } from 'vue';

const newTask=ref('');

const emit=defineEmits(['add-task']);


const handleSubmit=()=>{
    if(newTask.value.trim())return;

    emit('add-task',newTask.value);
    newTask.value='';

};


</script>

<template>
    <form @submit.prevent="handleSubmit" class="add-task">

       <input
       v-model="newTask" 
       placeholder="Enter a Task..."
       />
    
    
   <button type="submit">Add Task</button>

    </form>
</template> -->

<template>
  <form @submit.prevent="submit">
    <input v-model="text" placeholder="Enter task" />
    <button type="submit">Add</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-task'])
const text = ref('')

function submit () {
  if (!text.value.trim()) return
  emit('add-task', text.value)      
  text.value = ''
}
</script>

<style scoped>

.add-task {
  display: flex;
  gap: 12px;
  margin-bottom: 20px;
}

.add-task input {
  flex: 1;
  padding: 12px;
  border-radius: 6px;
  border: none;
  outline: none;
  font-size: 15px;
  background: #2a2a2a;
  color: #fff;
}

.add-task button {
  padding: 12px 20px;
  background: #42b983;
  color: #fff;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-size: 15px;
  font-weight: bold;
  transition: 0.2s;
}

.add-task button:hover {
  opacity: 0.9;
}

</style>

