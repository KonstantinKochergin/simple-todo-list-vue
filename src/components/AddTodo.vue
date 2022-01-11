<template>
  <form @submit.prevent class="container mb-5">
      <div class="inputs-group">
        <label for="title">Title:</label>
        <input type="text" name="title" v-model="todo.title">
      </div>
      <div class="inputs-group">
        <label for="description">Description:</label>
        <input type="text" name="description" v-model="todo.description">
      </div>
      <button class="btn btn-success" @click="createTodo">Create</button>
  </form>
</template>

<script>
export default {
  name: 'add-todo',
  data() {
    return {
      todo: {
        id: "",
        title: "",
        description: "",
      }
    } 
  },
  methods: {
    createTodo() {
      this.todo.id = Date.now().toString()
      this.$emit('add-todo', this.todo)
      this.todo = {
        title: "",
        description: ""
      }
    }
  }
}
</script>

<style>
.inputs-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 5px;
}

.inputs-group:last-child {
  margin-bottom: 0;
}
</style>