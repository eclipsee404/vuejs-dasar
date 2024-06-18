<script setup>
import { ref, defineEmits } from "vue";
const todo = ref("");
// const clearTodo = () => {
//   todo = "";
// };
const emits = defineEmits(["addTodo"]);
const clear = () => {
  todo.value = "";
};
</script>
<template>
  <h1>Form Todo's</h1>
  <form @submit.prevent="emits('addTodo', { todo, clear })">
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">Todo</label>
      <input type="text" v-model="todo" class="form-control" />
    </div>
    <button class="btn btn-primary">Add</button>
  </form>
</template>
