<template>
    <div class="flex items-center justify-center min-h-screen bg-grey-50">
      <div class="w-full max-w-xs">
        <div class="relative h-1 w-full bg-gray-200">
          <div class="absolute top-0 left-0 h-full bg-blue-500" :class="{'animate-progress': true}"></div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    mounted() {
      setTimeout(() => {
        this.$router.push('/classes');
      }, 1000); // Redirect after 1 second
    },
  }
  </script>
  
  <style>
  @keyframes loadProgress {
    0% {
      width: 0%;
    }
    100% {
      width: 100%;
    }
  }
  .animate-progress {
    animation: loadProgress 1s ease-out forwards;
  }
  </style>
  