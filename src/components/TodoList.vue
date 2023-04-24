<template>
  <div v-for="(task, index) in todos" :key="index">
    <ul class="tasks mt-2">
      <li class="task">
        <span :style="{ textDecoration: task.checked ? 'line-through' : 'none' }">{{ task.name }}</span>
        <input class="box" type="checkbox" v-model="task.checked" />
        <button class="btn btn-danger delete" @click="deleteTodo(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['todos'],
  emits: ['update-todos'],
  setup(props, { emit }) {
    const deleteTodo = (index) => {
      const newTodos = [...props.todos];
      newTodos.splice(index, 1);
      emit('update-todos', newTodos);
    };

    return { deleteTodo };
  },
};
</script>

<style scoped>
.tasks {
  list-style: none;
}

.box {
  margin-left: 10px;
}

.delete {
  font-size: 0.5em !important;
  padding: 3px 6px 3px 6px;
  margin-left: 10px;
}
</style>
