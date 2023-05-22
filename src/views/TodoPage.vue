<script setup>
import { ref, computed } from 'vue'
import TodoList from '@/components/TodoList.vue'
import TodoForm from '@/components/TodoForm.vue'

const todos = ref([
  { id: 1, text: 'Learn JavaScript', done: false },
  { id: 2, text: 'Learn Vue', done: false },
  { id: 3, text: 'Play around in JSFiddle', done: true },
  { id: 4, text: 'Build something awesome', done: true }
])

const displayType = ref('all')
const doneTodos = computed(() => todos.value.filter((todo) => todo.done))
const activeTodos = computed(() => todos.value.filter((todo) => !todo.done))
const doneCount = computed(() => doneTodos.value.length)

const addTodo = (todo) => {
  todos.value.push({
    id: todos.value.length + 1,
    text: todo,
    done: false
  })
}
</script>

<template>
  <div>
    <TodoForm @add-todo="addTodo" />
    <hr />
    <h2>Done todo count:{{ doneCount }}</h2>

    <select v-model="displayType">
      <option value="all">All</option>
      <option value="active">Active</option>
      <option value="done">Done</option>
    </select>
    <TodoList v-if="displayType === 'all'" :todos="todos" />
    <TodoList v-else :todos="displayType === 'active' ? activeTodos : doneTodos" />
  </div>
</template>

<style scoped>
select {
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 10px;
  margin-right: 8px;
  font-size: 1rem;
}
</style>
