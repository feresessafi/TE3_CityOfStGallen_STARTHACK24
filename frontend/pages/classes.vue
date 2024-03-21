<template>
  <div
    class="min-h-screen flex flex-col items-center justify-center bg-gray-100 p-24"
  >
    <h1 class="text-8xl font-bold text-gray-900 mb-20">Your Classes</h1>
    <div class="flex flex-wrap justify-center gap-8">
      <button
        v-for="classs in classes"
        :key="classs.classname"

        class="flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-xl font-bold text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 min-w-[80px]"
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

