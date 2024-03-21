<template>
    <div class="fixed inset-0 flex items-center justify-center" @click.self="closeModal()" style="backdrop-filter: blur(10px); background-color: rgba(255, 255, 255, 0.1);">
      <div class="relative mx-auto p-6 bg-white rounded-md shadow-lg max-w-lg w-full" style="margin-top: 15%; margin-bottom: 15%;">
        <!-- Modal content -->
        <div class="flex items-start space-x-4">
          <img src="/images/demoStudentAvatar.png" alt="Avatar" class="w-16 h-16 rounded-full border-2 border-gray-200">
          <div class="flex-1">
            <h2 class="text-xl font-semibold text-gray-900">{{ student.firstname }} {{ student.lastname }}</h2>
            <p class="text-gray-500">Age: {{ student.age }}</p>
            <p class="text-gray-500">Class: Dynamic Class Placeholder</p>
          </div>
        </div>
        <div class="mt-4">
          <h3 class="text-lg font-medium text-gray-900">Top Strength</h3>
          <p class="text-gray-500">{{ student.topstrength }}</p>
          <h3 class="text-lg font-medium text-gray-900 mt-3">Weaknesses</h3>
          <ul class="list-disc pl-5 text-gray-500">
            <li>{{ student.weakness1 }}</li>
            <li>{{ student.weakness2 }}</li>
          </ul>
        </div>
        <div class="mt-5">
          <button class="py-2 px-4 bg-gray-900 text-white rounded hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-gray-900 focus:ring-offset-2" @click="closeModal()">Close</button>
        </div>
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
  