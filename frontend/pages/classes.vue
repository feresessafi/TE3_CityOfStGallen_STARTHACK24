<template>
    <div>
      <h1>Your Classes</h1>
      <div v-if="classes.length === 0">Loading...</div>
      <div v-else>
        <button
          v-for="(classData, index) in classes"
          :key="index"
          
          class="class-button"
        >
          {{ classData.classname }}
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
          const response = await fetch('/classes.json');
          if (!response.ok) {
            throw new Error('Failed to fetch classes');
          }
          const data = await response.json();
          this.classes = data;
        } catch (error) {
          console.error('Error fetching classes:', error);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add your CSS styles here */
  .class-button {
    display: inline-block;
    padding: 10px 20px;
    margin: 5px;
    font-size: 16px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .class-button:hover {
    background-color: #0056b3;
  }
  </style>
  