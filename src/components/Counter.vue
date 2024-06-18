<script setup>
import { ref, defineEmits } from "vue";

const count = ref(0);
const emit = defineEmits(["showCounter"]);
const showAllert = (isPlus) => {
  if (isPlus) {
    count.value++;
  } else {
    count.value--;
  }
  emit("showCounter", count.value);
};
</script>
<template>
  <h1>Counter Example</h1>
  <button class="btn btn-sm btn-danger" @click="showAllert(false)">-</button>
  <button class="btn btn-sm btn-success" @click="showAllert(true)">+</button>
</template>
