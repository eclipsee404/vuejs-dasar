<script setup>
import { ref, onMounted } from "vue";
import Counter from "./components/Counter.vue";
import FormsTodos from "./components/FormTodos.vue";
import ListTodos from "./components/ListTodos.vue";
const hasil = ref(0);
const resultCounter = (data) => {
  // alert(data);
  hasil.value = data;
};

const todos = ref([]);

onMounted(() => {
  const data = JSON.parse(localStorage.getItem("todos"));
  if (data) {
    todos.value = data;
  }
});

function save() {
  localStorage.setItem("todos", JSON.stringify(todos.value));
}

const showResultTodo = (data) => {
  if (data.todo != "") {
    todos.value.push({ id: crypto.randomUUID(), todo: data.todo });
    save();
  } else {
    alert("please insert todo");
  }
  data.clear();
};

const deleteTodo = (id) => {
  todos.value = todos.value.filter((item) => item.id != id);
  save();
};
</script>

<template>
  <Counter @show-counter="resultCounter"></Counter>

  <h1>
    Hasil =

    <b v-if="hasil >= 0">{{ hasil }}</b>
    <b v-else>0</b>
  </h1>

  <hr />

  <FormsTodos @add-todo="showResultTodo"></FormsTodos>
  <ListTodos v-bind:todos="todos" @delete-todos="deleteTodo"></ListTodos>
</template>
