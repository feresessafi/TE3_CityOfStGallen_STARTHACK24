<template>
    <div class="min-h-screen flex items-center justify-center bg-gray-100">
        <div class="max-w-md w-full bg-white rounded-lg shadow-md p-8">
            <div class="mb-4">
                <h2 class="text-center text-2xl font-bold text-gray-900">Login</h2>
            </div>
            <form @submit.prevent="submitForm" class="space-y-6">
                <div>
                    <label for="username" class="text-sm font-medium text-gray-700">Username</label>
                    <input type="text" id="username" v-model="credentials.username"
                        class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
                        required>
                </div>
                <div>
                    <label for="password" class="text-sm font-medium text-gray-700">Password</label>
                    <input type="password" id="password" v-model="credentials.password"
                        class="mt-1 block w-full p-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
                        required>
                </div>
                <div>
                    <button type="submit"
                        class="w-full flex justify-center py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">Sign
                        In</button>
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
            // Here you would handle the login logic, potentially sending the credentials to your backend server for authentication
        },
    },
};
</script>
