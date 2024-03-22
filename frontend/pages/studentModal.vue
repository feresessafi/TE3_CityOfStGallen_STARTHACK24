<template>
  <div
    class="fixed inset-0 bg-white bg-opacity-60 backdrop-blur-sm flex items-center justify-center p-4"
    @click.self="closeModal()"
  >
    <div
      class="bg-white rounded-2xl shadow-xl max-w-lg w-full p-6 border border-gray-100 overflow-hidden"
      @click.stop
    >
      <div class="flex justify-between items-center mb-6">
        <h2 class="text-2xl font-semibold text-gray-800">
          {{ student.firstname }} {{ student.lastname }}
        </h2>
        <img
          src="/images/avatar.png"
          alt="Student Avatar"
          class="w-20 h-20 mt-7 rounded-full border-2 border-orange-300"
        />
        
      </div>
      <div class="text-gray-600 space-y-4 mb-6">
        <p class="text-grey-150">
          Age:<span class="pl-1 font-medium"> {{ student.age }} </span>
        </p>
        <p class="text-grey-150">
          Class:<span class="pl-1 font-medium"> {{ student.class }} </span>
        </p>

        <div>
          <h3 class="font-medium font-bold text-lg text-indigo-500">
            Key Strengths
          </h3>
          <ul class="list-none pl-5">
            <li class="pt-1">{{ student.topstrength }}</li>
            <!-- Assuming there might be more than one strength, adjust accordingly -->
          </ul>
        </div>
        <div>
          <h3 class="font-medium text-lg font-bold text-indigo-500">
            Growth Opportunities
          </h3>
          <ul class="list-none pl-5">
            <li class="pt-1">{{ student.weakness1 }}</li>
            <li class="pt-1">{{ student.weakness2 }}</li>
          </ul>
        </div>
        <div>
          <h3 class="font-medium font-bold text-lg text-indigo-500">
            Focused Preperation for Upcoming Topics
          </h3>
          <ul class="list-none pl-5">
            <ul>
              <li>
                <span class="font-semibold">Next: </span>Advanced Fractions
              </li>
              <li>
                <span class="font-semibold">Focus: </span>Practice simple
                fractions with visual aids
              </li>
            </ul>
          </ul>
        </div>
        <!-- implement the functionality here-->

        <div class="space-y-4 mb-6">
          <!-- New Observation Logging Section -->
          <h3 class="font-medium font-bold text-lg text-indigo-500">
            Class Observations
          </h3>

          <textarea
            v-model="observation"
            placeholder="Enter observations here..."
            class="w-full p-2 border border-gray-300 rounded-lg focus:ring-blue-500 focus:border-blue-500"
          ></textarea>
          <button
            :class="{
              'bg-green-500': buttonClicked,
              'bg-blue-500 hover:bg-blue-600': !buttonClicked,
            }"
            class="py-2 px-4 text-white font-medium rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-colors duration-300"
            @click="logObservation"
          >
            Log Observation
          </button>
        </div>

        <!-- end the functionality here-->
      </div>
      <div class="flex justify-end">
        <button
          class="py-2 px-4 bg-red-500 hover:bg-red-600 text-white font-medium rounded-lg focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2"
          @click="closeModal()"
        >
          Close
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    student: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      observation: "",
      buttonClicked: false, // To handle the button color change
    };
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
    logObservation() {
      console.log("Observation:", this.observation); // Handle the observation logging as needed
      this.buttonClicked = true; // Change button to green

      // Clear the observation field
      this.observation = ""; // Reset observation to empty

      setTimeout(() => {
        this.buttonClicked = false; // Revert button color after 1 second
      }, 1000);
    },
  },
};
</script>
