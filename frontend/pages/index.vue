<template>
  <div id="app" class="font-sans bg-white p-4">
    <h1 class="text-xl font-bold text-gray-800 mb-4">Students</h1>
    <ul class="list-disc pl-5">
      <li v-for="student in students" :key="student.firstname" class="mb-3">
        <div class="text-lg font-medium text-gray-900">
          {{ student.firstname }} {{ student.lastname }} - Age: {{ student.age }}
        </div>
        <ul class="mt-1 ml-4 list-inside list-disc">
          <li class="text-gray-700">Top Strength: {{ student.topstrength }}</li>
          <li class="text-gray-700">Weakness 1: {{ student.weakness1 }}</li>
          <li class="text-gray-700">Weakness 2: {{ student.weakness2 }}</li>
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
