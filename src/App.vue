<template>
  <h1>Interview Vue3 Junior</h1>
  <h2 class="mt-3">Task 1: Counter</h2>
  <Counter />
  <h2 class="mt-4" >Task 2: People API</h2>
  <People />
  <h2 class="mt-4" >Task 3: Todo List With Props</h2>
  <Todo />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Counter from './components/Counter.vue'
import People from './components/People.vue'
import Todo from './components/Todo.vue'

export default defineComponent({
  name: 'App',
  components: {Counter, People, Todo}
});
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
