<template>
  <div
    class="min-h-screen flex flex-col items-center justify-center bg-gray-50 p-24"
  >
    <h1 class="text-8xl font-bold text-gray-800 mb-20">Your Classes</h1>
    <div class="flex flex-wrap justify-center gap-8">
      <button
        v-for="classs in classes"
        :key="classs.classname"
        class="transition ease-in-out duration-150 flex justify-center py-2 px-4 border border-transparent rounded-md shadow text-xl font-medium text-white bg-indigo-500 hover:bg-indigo-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
        @click="$router.push('/students')"
      >
        {{ classs.classname }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      classes: [],
    };
  },
  mounted() {
    this.fetchClasses();
  },
  methods: {
    async fetchClasses() {
      try {
        const response = await fetch("/classes.json");
        if (!response.ok) {
          throw new Error("Failed to fetch classes");
        }
        const data = await response.json();
        this.classes = data;
      } catch (error) {
        console.error("Error fetching classes:", error);
      }
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
