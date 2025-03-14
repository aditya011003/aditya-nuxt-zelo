<template>
  <div class="flex flex-col md:flex-row gap-6">
    <!-- Map Section -->
    <div class="bg-white shadow-lg rounded-2xl p-4 w-full md:w-1/2">
      <h2 class="text-lg font-semibold text-gray-800 mb-4">{{ mapTitle }}</h2>
      <div class="relative w-full h-64 rounded-lg overflow-hidden">
        <iframe
          :src="mapSrc"
          class="absolute inset-0 w-full h-full border-none"
          allowfullscreen=""
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
        ></iframe>
      </div>
    </div>

    <!-- Information Section -->
    <div class="flex flex-col w-full md:w-1/2 space-y-4">
      <div
        v-for="(section, index) in infoSections"
        :key="index"
        class="bg-white border border-gray-300 shadow-md rounded-2xl p-4"
      >
        <h2 class="text-lg font-semibold text-gray-800 mb-2">
          {{ section.title }}
        </h2>
        <div
          v-if="section.icon"
          class="flex items-center space-x-2 text-gray-700"
        >
          <img :src="section.icon" alt="Icon" class="w-5 h-5" />
          <span>{{ section.description }}</span>
        </div>
        <div v-else class="flex flex-wrap gap-2">
          <span
            v-for="(item, i) in section.items"
            :key="i"
            class="border border-gray-300 text-gray-700 px-3 py-1 rounded-lg text-sm"
          >
            {{ item }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

defineProps({
  mapTitle: {
    type: String,
    default: "Map Location",
  },
  mapSrc: {
    type: String,
    required: true,
  },
  infoSections: {
    type: Array,
    required: true,
  },
});
</script>
