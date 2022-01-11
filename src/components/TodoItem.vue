<template>
  <div class="card mb-4">
      <div class="card-header">{{todo.title}}</div>
      <div class="card-body">{{todo.description}}</div>
      <button class="btn btn-danger" @click="deleteTodo">Delete</button>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    todo: {
      type: Object,
      required: true,
    }
  },
  methods: {
    deleteTodo() {
      this.$emit('delete-todo', this.todo)
    }
  }
}
</script>

<style>

</style>