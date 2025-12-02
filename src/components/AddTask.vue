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

.add-task{
    display:flex;
    gap:10px;
    margin-bottom:20px;

}

input{

    flex:1;
    padding:10px;
    border-radius:4px;
    border:none;
    outline:none;


}

button{
    padding:10px 16px;
    background: #42b983;
    border:none;
    color:#fff;
    border-radius: 4px;
    cursor:pointer;
    font-weight: bold;

}
button:hover{
   opacity:0.9;
}



</style>

