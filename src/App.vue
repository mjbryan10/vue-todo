<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Spinner v-if="isLoading" />
    <Todos v-else v-bind:todos="todos" v-on:del-todo="deleteTodo" v-on:check-todo="markComplete" />
  </div>
</template>

<script>
import Todos from './components/Todos.vue'
import Header from './components/layout/Header.vue';
import AddTodo from './components/AddTodo';
import Spinner from './components/Spinner'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
    Spinner
  },
  data() {
    return {
      todos: [
       
      ],
      isLoading: false,
      error: "",
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => id !== todo.id);
    },
    markComplete(id) {
      const target = this.todos.find(todo => todo.id === id)
          target.completed = !target.completed;
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    this.error = "";
    this.isLoading = true;
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => {
        this.todos = res.data;
        this.isLoading = false;
        })
      .catch(err => {
        console.log(err)
        this.error = "Oops something went wrong, please try again later.";
        })
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn { 
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
#app {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
