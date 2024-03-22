<template>
  <div class="flex flex-col items-center justify-center min-h-screen bg-gray-50 top-0"> <!-- pt-12 reduces the top padding, effectively moving content up -->
    <div class="flex items-center justify-center mb-8 space-x-4"> <!-- space-x-4 adds spacing between logo and text -->
      <img src="public/images/LogoTE3.png" alt="TE3 Logo" class="w-48 h-48"> <!-- Adjust size as needed -->
      <h1 class="text-8xl font-bold text-gray-800">TE3</h1>
    </div>
    <h2 class="text-6xl font-bold animate-text-change pt-12">Transforming Evaluation Experience.</h2>
  </div>
</template>

<script>
export default {
  mounted() {
    setTimeout(() => {
      this.$router.push('/login'); // Adjust this as necessary
    }, 3000); // Delay before redirect
  },
};
</script>

<style>
@keyframes textColorChange {
  0%, 100% {
    color: #6366f1; /* Tailwind's indigo-500 */
  }
  50% {
    color: #f0a148; /* Tailwind's gray-400 */
  }
}
.animate-text-change {
  animation: textColorChange 3s ease-in-out forwards infinite;
}
</style>
