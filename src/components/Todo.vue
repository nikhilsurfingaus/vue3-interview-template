<template>
    <div>
        <input v-model="newTodoName" type="text" placeholder="New Task" @keydown.enter="addTodo" />
    </div>
    <div>
        <TodoList :todos="todos" @update-todos="updateTodos" v-model="todos" />
    </div>
</template>

<script>
import { ref } from 'vue';
import TodoList from './TodoList.vue';
    export default {
        components: { TodoList },
        setup() {

            const newTodoName = ref(null)
            const todos = ref([])


            const addTodo = () => {
                const newTodo = {
                    name: newTodoName.value,
                    checked: false
                }
                todos.value = [...todos.value, newTodo]
                newTodoName.value = null
                console.log(todos.value)
            }

            const updateTodos = (newTodos) => {
                todos.value = newTodos;
            };

            return {newTodoName, addTodo, todos, updateTodos}
        }
    }
</script>

<style scoped>

</style>