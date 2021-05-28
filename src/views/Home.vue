<template>
  <div id="app">
    <CreateTodoItem v-on:create-todo="addTodoItem"/>
    <TodoList v-bind:items="todos" v-on:delete-todo="deleteTodoItem"/>
  </div>
</template>

<script>
import TodoList from '../components/TodoList'
import CreateTodoItem from '../components/CreateTodoItem.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    TodoList,
    CreateTodoItem
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodoItem(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(() => this.todos = this.todos.filter(item => item.id !== id))
      .catch(e => console.log(e));
    },
    addTodoItem(todo) {
      const { title, completed} = todo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(response => this.todos = [...this.todos, response.data])
      .catch(e => console.log(e));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=7')
    .then(response => this.todos = response.data)
    .catch(e => console.log(e));
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
