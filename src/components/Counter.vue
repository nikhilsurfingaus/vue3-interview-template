<template>
  <div class="container mt-5">
    <p class="fw-bold">Current Count: {{ count }}</p>
    <div class="operations">
      <button @click="handleClick('increment')" class="btn btn-primary">+</button>
      <button @click="handleClick('decrement')" class="btn btn-primary">-</button>
    </div>
    <div class="custom d-flex justify-content-center">
      <input type="text" class="form-control w-50" v-model="inputCount" placeholder="Count" @keydown.enter="handleClick('custom')" />
    </div>
    <div>
      <button @click="handleClick('reset')" class="btn btn-danger mt-4">Reset Counter</button>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const count = ref(0);
    const inputCount = ref("");

    const handleClick = (payload) => {
      switch (payload) {
        case "increment":
          count.value++;
          break;
        case "decrement":
          count.value--;
          break;
        case "reset":
          count.value = 0;
          break;
        case "custom":
          const customCount = parseInt(inputCount.value);
          if (!isNaN(customCount)) {
            count.value += customCount;
          }
          inputCount.value = "";
          break;
        default:
          break;
      }
    };

    return { count, handleClick, inputCount };
  },
};
</script>

<style scoped>
.custom {
  margin-top: 20px;
}
</style>
