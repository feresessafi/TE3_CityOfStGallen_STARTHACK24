<template>
    <div class="min-h-screen flex items-center justify-center bg-blue-50">
      <div class="max-w-md w-full bg-white rounded-lg shadow-lg p-10">
        <div class="mb-8">
          <h2 class="text-center text-3xl font-semibold text-gray-900">Login</h2>
        </div>
        <form @submit.prevent="submitForm" class="space-y-8">
          <div>
            <label for="username" class="block text-lg font-medium text-gray-800">Username</label>
            <input type="text" id="username" v-model="credentials.username"
              class="mt-2 block w-full p-3 border border-gray-300 rounded-md shadow-sm text-gray-700 focus:outline-none focus:ring-blue-300 focus:border-blue-300"
              required>
          </div>
          <div>
            <label for="password" class="block text-lg font-medium text-gray-800">Password</label>
            <input type="password" id="password" v-model="credentials.password"
              class="mt-2 block w-full p-3 border border-gray-300 rounded-md shadow-sm text-gray-700 focus:outline-none focus:ring-blue-300 focus:border-blue-300"
              required>
          </div>
          <div>
            <button type="submit"
              class="w-full flex justify-center py-3 px-4 border border-transparent rounded-md shadow-sm text-lg font-medium text-white bg-blue-500 hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
              Sign In
            </button>
          </div>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        credentials: {
          username: '',
          password: '',
        },
      };
    },
    methods: {
      submitForm() {
        console.log('Submitting:', this.credentials);
        // Handle login logic here
        this.$router.push('/classes'); // Adjust according to your routing
      },
    },
  };
  </script>
  