<template>
    <div class="mt-6 px-6 w-full max-w-5xl mx-auto">
      <!-- Section Header -->
      <h2 class="text-lg font-semibold text-gray-900">Matrices</h2>
  
      <!-- Toggle State/National -->
      <div class="flex justify-between items-center mt-4">
        <div class="bg-gray-200 p-1 rounded-lg flex">
          <button
            @click="activeTab = 'state'"
            :class="[
              'px-4 py-2 rounded-lg text-sm font-medium',
              activeTab === 'state' ? 'bg-gray-900 text-white' : 'text-gray-700',
            ]"
          >
            State Avg.
          </button>
          <button
            @click="activeTab = 'national'"
            :class="[
              'px-4 py-2 rounded-lg text-sm font-medium',
              activeTab === 'national' ? 'bg-gray-900 text-white' : 'text-gray-700',
            ]"
          >
            National Avg.
          </button>
        </div>
  
        <!-- Navigation Buttons -->
        <div class="flex space-x-2">
          <button @click="scrollLeft" class="p-2 bg-gray-200 rounded-md">
            ◀
          </button>
          <button @click="scrollRight" class="p-2 bg-gray-200 rounded-md">
            ▶
          </button>
        </div>
      </div>
  
      <!-- Matrices Container (Scrollable) -->
      <div ref="scrollContainer" class="relative mt-4 flex overflow-x-auto space-x-4 scrollbar-hide scroll-snap">
        <div
          v-for="(item, index) in selectedData"
          :key="index"
          class="bg-white shadow rounded-lg p-4 w-56 flex-shrink-0 text-center border border-gray-200 snap-start"
        >
          <!-- Dynamic Graph -->
          <div class="relative mx-auto w-24 h-24">
            <svg viewBox="0 0 100 100" class="w-full h-full">
              <circle
                cx="50"
                cy="50"
                r="45"
                fill="transparent"
                stroke="gray"
                stroke-width="8"
                stroke-opacity="0.2"
              />
              <circle
                cx="50"
                cy="50"
                r="45"
                fill="transparent"
                :stroke="item.color"
                stroke-width="8"
                stroke-linecap="round"
                :stroke-dasharray="getStrokeDasharray(item.percentage)"
                stroke-dashoffset="25"
              />
            </svg>
            <div class="absolute inset-0 flex flex-col items-center justify-center text-gray-800">
              <span class="text-lg font-semibold">Top {{ item.rank }}</span>
              <span class="text-sm text-gray-500">{{ item.performance }}</span>
            </div>
          </div>
  
          <!-- Label -->
          <p class="mt-2 text-gray-700 text-sm">{{ item.label }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from "vue";
  
  const activeTab = ref("state");
  const scrollContainer = ref(null);
  
  const stateData = ref([
    { rank: 10, performance: "Excellent", label: "Upper limb (arm)", percentage: 90, color: "green" },
    { rank: 25, performance: "Very Good", label: "Coronary angiop", percentage: 75, color: "blue" },
    { rank: 40, performance: "Good", label: "Prostate resect", percentage: 60, color: "skyblue" },
    { rank: 50, performance: "Average", label: "Carotid endarterectomy", percentage: 50, color: "gold" },
  ]);
  
  const nationalData = ref([
    { rank: 15, performance: "Very Good", label: "Heart Surgery", percentage: 85, color: "green" },
    { rank: 30, performance: "Good", label: "Knee Replacement", percentage: 70, color: "blue" },
    { rank: 45, performance: "Average", label: "Spinal Surgery", percentage: 55, color: "orange" },
    { rank: 60, performance: "Below Average", label: "Lung Surgery", percentage: 40, color: "red" },
  ]);
  
  const selectedData = computed(() => (activeTab.value === "state" ? stateData.value : nationalData.value));
  
  const getStrokeDasharray = (percentage) => {
    const circumference = 2 * Math.PI * 45;
    return `${(percentage / 100) * circumference} ${circumference}`;
  };
  
  const scrollLeft = () => {
    scrollContainer.value.scrollBy({ left: -220, behavior: "smooth" });
  };
  
  const scrollRight = () => {
    scrollContainer.value.scrollBy({ left: 220, behavior: "smooth" });
  };
  </script>
  
  <style>
  /* Hide Scrollbar */
  .scrollbar-hide::-webkit-scrollbar {
    display: none;
  }
  .scrollbar-hide {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
  
  /* Enable Smooth Scrolling */
  .scroll-snap {
    scroll-snap-type: x mandatory;
  }
  .snap-start {
    scroll-snap-align: start;
  }
  </style>
  