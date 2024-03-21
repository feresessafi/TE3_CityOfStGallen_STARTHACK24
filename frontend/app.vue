<template>
  <div id="app">
    <h1>Students</h1>
    <ul>
      <li v-for="student in students" :key="student.firstname">
        {{ student.firstname }} {{ student.lastname }} - Age: {{ student.age }}
        <ul>
          <li>Top Strength: {{ student.topstrength }}</li>
          <li>Weakness 1: {{ student.weakness1 }}</li>
          <li>Weakness 2: {{ student.weakness2 }}</li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const students = ref([]);

onMounted(async () => {
  const response = await fetch('students.json');
  students.value = await response.json();
});
</script>

<style>
/* Add styles as needed */
</style>
