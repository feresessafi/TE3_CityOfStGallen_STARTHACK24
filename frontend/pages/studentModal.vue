<template>
    <div class="fixed inset-0 bg-white bg-opacity-60 backdrop-blur-sm flex items-center justify-center p-4" @click.self="closeModal()">
      <div class="bg-white rounded-2xl shadow-xl max-w-lg w-full p-6 border border-gray-100 overflow-hidden" @click.stop>
        <div class="flex justify-between items-center mb-6">
          <h2 class="text-2xl font-semibold text-gray-800">{{ student.firstname }} {{ student.lastname }}</h2>
          <img src="/images/demoStudentAvatar.png" alt="Student Avatar" class="w-12 h-12 rounded-full border-2 border-orange-300">
        </div>
        <div class="text-gray-600 space-y-4 mb-6">
          <p><span class="font-medium">Age:</span> {{ student.age }}</p>
          <p><span class="font-medium">Class:</span> {{ student.class }}</p>
          <div>
            <h3 class="font-medium text-lg">Top Strengths</h3>
            <ul class="list-disc pl-5">
              <li>{{ student.topstrength }}</li>
              <li>{{ student.topstrength }}</li>
            </ul>
          </div>
          <div>
            <h3 class="font-medium text-lg">Key Weaknesses</h3>
            <ul class="list-disc pl-5">
              <li>{{ student.weakness1 }}</li>
              <li>{{ student.weakness2 }}</li>
            </ul>
          </div>
        </div>
        <div class="flex justify-end">
          <button class="py-2 px-4 bg-blue-500 hover:bg-blue-600 text-white font-medium rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2" @click="closeModal()">Close</button>
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
  