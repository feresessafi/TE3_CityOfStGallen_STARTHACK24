<template>
  <div
    class="dynamic-background flex flex-col items-center justify-center p-24"
  >
    <h1 class="text-8xl font-bold text-blue-900 mb-20">Your Classes</h1>
    <div class="flex flex-wrap justify-center gap-8">
      <button
        v-for="classs in classes"
        :key="classs.classname"
        class="relative inline-flex items-center justify-center p-0.5 overflow-hidden text-xl font-medium text-blue-900 rounded-lg group bg-gradient-to-br from-orange-200 via-blue-200 to-orange-200 group-hover:from-orange-300 group-hover:via-blue-300 group-hover:to-orange-300 hover:text-blue-900 focus:ring-4 focus:outline-none focus:ring-orange-200"

        @click="$router.push('/students')"
      >
      <span
          class="relative px-5 py-2.5 transition-all ease-in duration-75 bg-white rounded-md group-hover:bg-opacity-0"
      >
        {{ classs.classname }}        
      </span>
        
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
