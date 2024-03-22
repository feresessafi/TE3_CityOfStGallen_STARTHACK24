<template>
    <nav class="fixed top-0 w-full bg-white shadow z-50">
      <div class="max-w-7xl mx-auto px-2 sm:px-4 lg:px-6">
        <div class="flex justify-between h-12 items-center">
          <div class="flex-shrink-0 flex items-center">
            <img src="/images/LogoTE3.png" alt="Logo" class="h-7 pr-2 rounded-full w-auto"/>
            <h2 class="text-md font-semibold text-gray-800 ml-1">TE3: Transforming Evaluation Experience</h2>
          </div>
          <!-- Increased margin on the left of the links container to move it further right -->
          <div class="hidden md:flex ml-auto mr-4"> <!-- Adjusted margin left (ml-auto) and added margin right (mr-4) -->
            <div class="flex items-baseline space-x-4">
              <router-link to="/" class="text-gray-800 hover:text-indigo-500 px-3 py-2 rounded-md text-md font-medium">Home</router-link>
              <router-link to="/classes" class="text-gray-800 hover:text-indigo-500 px-3 py-2 rounded-md text-md font-medium">Classes</router-link>
              <router-link to="/students" class="text-gray-800 hover:text-indigo-500 px-3 py-2 rounded-md text-md font-medium">Plans</router-link>
            </div>
          </div>
          <div class="flex items-center">
            <img src="/images/user.png" alt="Profile" class="h-8 w-8 rounded-full"/>
          </div>
        </div>
      </div>
    </nav>
  </template>
  
  
  <script>
  export default {
    name: "NavBar",
  };
  </script>
  
  <style>
  /* Additional custom styles if needed */
  </style>
  