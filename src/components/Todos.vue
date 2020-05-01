<template>
  <div class="hello">
    <div v-for="todo in todos" v-bind:key="todo.id">
      <TodoItem v-bind:todo="todo"/>
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
