<script setup>
import { ref, reactive } from "vue";

// Ref para tipos primitivos como strings, numeros, booleans, etc.
let count = ref(0);

// Reactive para tipos compostos como objetos, arrays, etc.
let courses = reactive([
  {
    title: "Vue.js",
  },
  {
    title: "React.js",
  },
  {
    title: "Blazor",
  },
]);

let newCourse = {};

function increment() {
  count.value++;
}

function addCourse() {
  courses.push(newCourse);
  newCourse = {};
}
</script>

<template>
  <div>
    <h1>{{ count }}</h1>
    <button @click="increment">Incrementar</button>
  </div>

  <div>
    <h1>Lista de cursos</h1>
    <ul>
      <li v-for="course of courses" :key="course.title">{{ course.title }}</li>
    </ul>
    <br />
    <input v-model="newCourse.title" type="text" />
    <button @click="addCourse">Adicionar</button>
  </div>
</template>

<style scoped></style>
