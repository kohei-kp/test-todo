<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  todos: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <ul class="todos">
    <li v-for="todo in props.todos" :key="todo.id" class="todo">
      <input type="checkbox" v-model="todo.done" :id="`todo-${todo.id}`" />
      <label :for="`todo-${todo.id}`">
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
      </label>
    </li>
  </ul>
</template>

<style scoped>
.todos {
  list-style: none;
  padding: 5px;
}
.todo {
  padding: 5px;
}
.done {
  text-decoration: line-through;
}

input[type='checkbox'] {
  margin-right: 8px;
}
</style>
