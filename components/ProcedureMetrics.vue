<template>
    <div class="mb-10 mt-6 px-6 w-full max-w-5xl mx-auto">
      <!-- Section Header -->
      <h2 class="text-lg font-semibold text-gray-900">Procedure Metrics</h2>
  
      <!-- Tab Navigation -->
      <div class="flex mt-4 bg-gray-100 p-1 rounded-lg w-fit">
        <button
          v-for="(tab, index) in tabs"
          :key="index"
          @click="activeTab = tab"
          :class="[
            'px-4 py-2 rounded-lg text-sm font-medium',
            activeTab === tab ? 'bg-gray-900 text-white' : 'text-gray-700',
          ]"
        >
          {{ tab }}
        </button>
      </div>
  
      <!-- Pills Container -->
      <div class="mt-4 flex flex-wrap gap-3">
        <div
          v-for="(item, index) in selectedData"
          :key="index"
          class="flex items-center bg-blue-50 text-gray-800 px-3 py-2 rounded-full text-sm shadow-md"
        >
          <span class="text-lg mr-2">💊</span> <!-- Common Icon -->
          {{ item.name }}
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from "vue";
  
  const activeTab = ref("Prescribed Medications");
  
  const tabs = ["Prescribed Medications", "Procedures", "Conditions"];
  
  const medications = ref([
    { name: "Amlodipine" },
    { name: "Metformin" },
    { name: "Lisinopril" },
    { name: "Levothyroxine" },
    { name: "Atorvastatin" },
    { name: "Albuterol" },
    { name: "Gabapentin" },
  ]);
  
  const procedures = ref([
    { name: "Knee Replacement" },
    { name: "Hip Surgery" },
    { name: "Cardiac Stent" },
    { name: "Appendectomy" },
    { name: "Gallbladder Removal" },
  ]);
  
  const conditions = ref([
    { name: "Diabetes" },
    { name: "Hypertension" },
    { name: "Asthma" },
    { name: "Arthritis" },
    { name: "Heart Disease" },
  ]);
  
  const selectedData = computed(() => {
    switch (activeTab.value) {
      case "Prescribed Medications":
        return medications.value;
      case "Procedures":
        return procedures.value;
      case "Conditions":
        return conditions.value;
      default:
        return [];
    }
  });
  </script>
  
  <style>
  /* Smooth transition for pill appearance */
  div.flex.flex-wrap.gap-3 > div {
    transition: all 0.3s ease-in-out;
  }
  </style>
  