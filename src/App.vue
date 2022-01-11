<template>
  <div id="app">
    <add-todo @add-todo="createTodo"/>
    <todo-list :todos="todos" @delete-todo="deleteTodo"/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import AddTodo from './components/AddTodo.vue'

export default {
  name: 'App',
  components: {TodoList, AddTodo},
  data() {
    return {
      todos: []
    }
  },
  mounted() {
    const saved = localStorage.getItem("TODOS")
    if (saved) {
      this.todos = JSON.parse(saved)
    }
  },
  methods: {
    createTodo(todo) {
      this.todos.push(todo)
      localStorage.setItem("TODOS", JSON.stringify(this.todos))
    },
    deleteTodo(td) {
      this.todos = this.todos.filter(todo => todo.id !== td.id)
      localStorage.setItem("TODOS", JSON.stringify(this.todos))
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
