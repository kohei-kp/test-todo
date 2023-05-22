<script setup>
import { ref, defineEmits } from 'vue'

const emits = defineEmits(['add-todo'])
const todo = ref('')

const addTodo = () => {
  emits('add-todo', todo.value)
  todo.value = ''
}
</script>

<template>
  <div>
    <input v-model="todo" />
    <button @click="addTodo">Add</button>
  </div>
</template>

<style scoped>
input {
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 10px;
  margin-right: 8px;
  font-size: 1rem;
}
button {
  border: 1px solid steelblue;
  border-radius: 4px;
  padding: 10px;
  background-color: steelblue;
  color: #eee;
  font-size: 1rem;
}
button:hover {
  opacity: 0.8;
  cursor: pointer;
}
</style>
