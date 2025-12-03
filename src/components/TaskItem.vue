<script setup>


//receive task from parent
const props=defineProps({
    task:{
        type:String,
        required:true
    }
});

const emit=defineEmits(["toggle-task","delete-task"]);


</script>

<template>
    <div class="task-item"
    :class="{completed:task.completed}"
    >
    <div class="left">

    <input
    type="checkbox"
    :checked="task.completed"
    @change="emit('toggle-task')"
    />
    <span>{{task.text}}</span>

    </div>

    <button @click="emit('delete-task')">x</button>
    
    
    
    </div>
</template>

<style scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #2a2a2a;
  padding: 12px 16px;
  border-radius: 6px;
  transition: 0.2s;
}

.task-item:hover {
  background: #333;
}

.left {
  display: flex;
  align-items: center;
  gap: 12px;
}

.task-item.completed span {
  text-decoration: line-through;
  opacity: 0.6;
}

button {
  background: #e74c3c;
  color: white;
  border: none;
  padding: 6px 10px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 14px;
  transition: 0.2s;
}

button:hover {
  opacity: 0.85;
}

</style>

