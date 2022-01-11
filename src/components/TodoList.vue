<template>
  <div class="container">
    <todo-item v-for="todo in todos" :key="todo.id" :todo="todo" @delete-todo="$emit('delete-todo', todo)"/>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
  name: 'todo-list',
  components: {
    TodoItem,
  },
  props: {
    todos: {
      type: Array,
      required: true
    }
  },
}
</script>

<style>

</style>