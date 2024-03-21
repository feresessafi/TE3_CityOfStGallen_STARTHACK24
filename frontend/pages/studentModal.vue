<template>
    <div class="fixed inset-0 bg-gray-600 bg-opacity-50 overflow-y-auto h-full w-full flex items-center justify-center" @click.self="closeModal()" style="backdrop-filter: blur(5px);">
      <div class="relative mx-auto p-5 border w-full max-w-md shadow-lg rounded-md bg-white" style="margin-top: 15%; margin-bottom: 15%;">
        <!-- Optional Avatar -->
        <div class="flex items-center space-x-4 mb-4">
          <img src="./public/images/demoStudentAvatar.png" alt="Avatar" class="w-12 h-12 rounded-full">
          <h2 class="text-xl font-semibold">{{ student.firstname }} {{ student.lastname }}</h2>
        </div>
        <!-- Student Info -->
        <div class="mb-4">
          <p>Age: {{ student.age }}</p>
          <p>Class: Dynamic Class Placeholder</p>
        </div>
        <!-- Strengths and Weaknesses -->
        <div>
          <h3 class="font-semibold">Top Strength</h3>
          <p>{{ student.topstrength }}</p>
          <h3 class="font-semibold mt-3">Weaknesses</h3>
          <ul>
            <li>{{ student.weakness1 }}</li>
            <li>{{ student.weakness2 }}</li>
          </ul>
        </div>
        <button class="mt-4 py-2 px-4 bg-red-500 text-white rounded hover:bg-red-700" @click="closeModal()">Close</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      student: {
        type: Object,
        required: true,
      },
    },
    methods: {
      closeModal() {
        this.$emit('close');
      },
    },
  };
  </script>
  