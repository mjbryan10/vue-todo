<template>
  <div class="hello">
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem :todo="todo" v-on:del-todo="$emit('del-todo', todo.id)" v-on:check-todo="$emit('check-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem';
export default {
  name: 'Todos',
  props: ["todos"],
  components: {
    TodoItem,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
