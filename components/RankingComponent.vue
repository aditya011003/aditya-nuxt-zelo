<template>
  <div class="bg-white shadow-lg rounded-2xl p-6 w-full">
    <!-- Header Section -->
    <div class="flex justify-between items-center mb-4">
      <h2 class="text-xl font-semibold text-gray-800">Ranking</h2>
      <div class="flex space-x-3">
        <button
          @click="prevRanking"
          class="w-10 h-10 flex items-center justify-center border border-gray-300 rounded-lg hover:bg-gray-200"
          :disabled="currentIndex === 0"
        >
          <img
            src="../assets/svgs/left-arrow.svg"
            alt="Previous"
            class="w-4 h-4"
          />
        </button>
        <button
          @click="nextRanking"
          class="w-10 h-10 flex items-center justify-center border border-gray-300 rounded-lg hover:bg-gray-200"
          :disabled="currentIndex === rankings.length - 1"
        >
          <img
            src="../assets/svgs/right-arrow.svg"
            alt="Next"
            class="w-4 h-4"
          />
        </button>
      </div>
    </div>

    <!-- Ranking Content -->
    <div class="flex items-center justify-between">
      <!-- State Ranking -->
      <div class="flex items-center space-x-6">
        <div class="relative flex items-center justify-center">
          <div class="w-32 h-32 bg-blue-100 rounded-full flex items-center justify-center border border-blue-200 shadow-inner">
            <img :src="rankings[currentIndex].state.icon" alt="State Ranking" class="w-16 h-16" />
          </div>
        </div>
        <div>
          <p class="text-gray-800 font-semibold text-lg">State Ranking</p>
          <p class="text-gray-600 text-sm leading-tight">{{ rankings[currentIndex].state.description }}</p>
        </div>
      </div>

      <!-- Divider -->
      <!-- <div class="w-[2px] h-20 bg-gray-300"></div> -->

      <!-- National Ranking -->
      <div class="flex items-center space-x-6">
        <div class="relative flex items-center justify-center">
          <div class="w-32 h-32 bg-blue-100 rounded-full flex items-center justify-center border border-blue-200 shadow-inner">
            <img :src="rankings[currentIndex].national.icon" alt="National Ranking" class="w-16 h-16" />
          </div>
        </div>
        <div>
          <p class="text-gray-800 font-semibold text-lg">National Ranking</p>
          <p class="text-gray-600 text-sm leading-tight">{{ rankings[currentIndex].national.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, ref } from "vue";

const props = defineProps({
  rankings: {
    type: Array,
    required: true,
    default: () => [
      {
        state: {
          icon: "../assets/svgs/state-ranking.svg",
          description: "In 13 Adult Specialties, In 4 Children’s Specialties",
        },
        national: {
          icon: "../assets/svgs/national-ranking.svg",
          description: "In 13 Adult Specialties, In 4 Children’s Specialties",
        },
      },
      {
        state: {
          icon: "../assets/svgs/state-ranking.svg",
          description: "In 10 Adult Specialties, In 3 Children’s Specialties",
        },
        national: {
          icon: "../assets/svgs/national-ranking.svg",
          description: "In 15 Adult Specialties, In 5 Children’s Specialties",
        },
      },
      {
        state: {
          icon: "../assets/svgs/state-ranking.svg",
          description: "In 8 Adult Specialties, In 2 Children’s Specialties",
        },
        national: {
          icon: "../assets/svgs/national-ranking.svg",
          description: "In 12 Adult Specialties, In 6 Children’s Specialties",
        },
      },
    ],
  },
});

// Current index for ranking sets
const currentIndex = ref(0);

// Navigate to the previous ranking
const prevRanking = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--;
  }
};

// Navigate to the next ranking
const nextRanking = () => {
  if (currentIndex.value < props.rankings.length - 1) {
    currentIndex.value++;
  }
};
</script>

<style scoped>
button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
