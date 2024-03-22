<template>
    <NavBar/>
  <section class="min-h-screen flex items-center justify-center bg-grey-50">
    <div class="flex flex-col items-center px-6 py-8 mx-auto w-full max-w-md bg-white rounded-lg shadow-lg">
      <div class="mb-6 w-full"> <!-- Ensures the container spans the full width -->
        <div class="flex justify-center items-center mb-3"> <!-- Centers content horizontally and aligns items vertically -->
          <img src="public/images/LogoTE3.png" alt="TE3 Logo" class="w-12 h-12">
          <p class="text-xl font-semibold ml-2">TE3</p> <!-- Adjusted margins for spacing -->
        </div>
        <h2 class="text-center text-2xl font-semibold text-gray-900">Sign in to your account</h2>
      </div>
      <form @submit.prevent="submitForm" class="w-full space-y-6">
        <div>
          <label for="username" class="block mb-2 text-sm font-medium text-gray-900">Username</label>
          <input type="text" id="username" v-model="credentials.username" placeholder="name@company.com"
            class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
            required>
        </div>
        <div>
          <label for="password" class="block mb-2 text-sm font-medium text-gray-900">Password</label>
          <input type="password" id="password" v-model="credentials.password" placeholder="••••••••"
            class="bg-gray-50 border border-gray-300 text-gray-900 rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5"
            required>
        </div>
        <div class="flex items-center justify-between">
          <div class="flex items-start">
            <div class="flex items-center h-5">
              <input id="remember" type="checkbox" class="w-4 h-4 border border-gray-300 rounded bg-gray-50 focus:ring-blue-500">
            </div>
            <div class="ml-3 text-sm">
              <label for="remember" class="text-gray-500">Remember me</label>
            </div>
          </div>
          <a href="#" class="text-sm text-blue-500 hover:underline">Forgot password?</a>
        </div>
        <button type="submit"
          class="w-full flex justify-center py-2.5 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-blue-500 hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
          Sign in
        </button>
        <p class="text-sm text-center text-gray-500">
          Don’t have an account yet? <a href="#" class="text-blue-500 hover:underline">Sign up</a>
        </p>
      </form>
    </div>
  </section>
</template>

<script>
import NavBar from './Navbar.vue'; // Adjust the path as necessary

export default {
  components: {
    NavBar,
  },
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
      this.$router.push('/loading');
    },
  },
};
</script>
