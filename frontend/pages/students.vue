<template>
  <div
    class="min-h-screen flex flex-col items-center justify-center bg-gray-100 p-24"
  >
    <h1 class="text-8xl font-bold text-gray-900 mb-20">Your Students</h1>
    <div class="flex flex-wrap justify-center gap-8">
      <button
        v-for="student in students"
        :key="student.firstname"
        class="flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-xl font-bold text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        @click="showModal(student)"

      >
        {{ student.firstname }} {{ student.lastname }}
      </button>
    </div>
    <!-- Use the modal component -->
    <StudentModal
      v-if="selectedStudent"
      :student="selectedStudent"
      @close="selectedStudent = null"
    />
  </div>
</template>

<script>
import StudentModal from './studentModal.vue'; 

export default {
  components: {
    StudentModal,
  },
  data() {
    return {
      students: [],
      selectedStudent: null,
    };
  },
  mounted() {
    this.fetchStudents();
  },
  methods: {
    async fetchStudents() {
      try {
        const response = await fetch("/students.json");
        if (!response.ok) {
          throw new Error("Failed to fetch students");
        }
        const data = await response.json();
        this.students = data;
      } catch (error) {
        console.error("Error fetching students:", error);
      }
    },
    showModal(student) {
      this.selectedStudent = student;
    },
  },
};
</script>
