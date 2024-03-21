<template>
  <div
    class="dynamic-background flex flex-col items-center justify-center p-24"
  >
    <h1 class="text-8xl font-bold text-blue-900 mb-20">Your Students</h1>
    <div class="flex flex-wrap justify-center gap-8">
      <button
        v-for="student in students"
        :key="student.firstname"
        class="relative inline-flex items-center justify-center p-0.5 overflow-hidden text-xl font-medium text-blue-900 rounded-lg group bg-gradient-to-br from-orange-200 via-blue-200 to-orange-200 group-hover:from-orange-300 group-hover:via-blue-300 group-hover:to-orange-300 hover:text-blue-900 focus:ring-4 focus:outline-none focus:ring-orange-200"
        @click="showModal(student)"
      >
        <span
          class="relative px-5 py-2.5 transition-all ease-in duration-75 bg-white rounded-md group-hover:bg-opacity-0"
        >
          {{ student.firstname }} {{ student.lastname }}
        </span>
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
import StudentModal from "./StudentModal.vue"; // Ensure this path is correct

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

<style>
@keyframes backgroundAnimation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

.dynamic-background {
  background: linear-gradient(270deg, #ffedd5e9, #dbeafee3);
  background-size: 400% 400%;
  animation: backgroundAnimation 30s ease infinite;
  min-height: 100vh;
}
</style>
