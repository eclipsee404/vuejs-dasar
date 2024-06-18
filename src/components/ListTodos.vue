<script setup>
import { ref, defineEmits } from "vue";
import DeleteTodos from "./DeleteTodos.vue";
defineProps({ todos: { type: Array, required: true } });
const emits = defineEmits(["deleteTodos"]);
</script>

<template>
  <br />
  <div v-if="todos.length > 0">
    <h3>Todo list</h3>
    <ul class="list-group" v-for="todo in todos" v-bind:key="todo.id">
      <li class="list-group-item">
        {{ todo.todo }}
        <DeleteTodos @click="emits('deleteTodos', [todo.id])" />
      </li>
    </ul>
  </div>
  <div v-else>No todo's data</div>
</template>
