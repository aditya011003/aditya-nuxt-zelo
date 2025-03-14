<template>
  <div class="bg-white rounded-xl shadow-md p-3 w-[400px] max-w-md border border-gray-200">
    <div class="flex items-center mb-3">
      <!-- Image Section -->
      <div v-if="imageSrc" class="rounded-lg shadow-md mr-3">
        <img src="../assets/svgs/avatar-1.svg" alt="Profile" class="" />
      </div>

      <div class="flex-1">
        <!-- Title and Verification -->
        <div class="flex items-center space-x-2">
          <h2 v-if="title" class="text-lg font-semibold text-[#222E39]">
            {{ title }}
          </h2>
          <img v-if="isVerified" src="../assets/svgs/verifiedBadge.svg" alt="verified" class="w-4 h-4" />
        </div>

        <!-- Rating -->
        <div v-if="ratingValue" class="flex items-center mt-0">
          <span v-for="star in 5" :key="star" class="text-base"
            :class="star <= ratingValue ? 'text-yellow-400' : 'text-gray-300'">
            ★
          </span>
          <span class="text-[#222E39] text-xs ml-2">{{ ratingValue }} Ratings</span>
        </div>

        <!-- Additional Info -->
        <div v-if="badge1 || badge2" class="flex items-center text-[#222E39] text-xs mt-2 space-x-3">
          <span v-if="badge1" class="flex items-center space-x-1">
            <img src="../assets/svgs/Education.svg" alt="education" class="w-3 h-3" />
            <span class="font-medium">{{ badge1 }}</span>
          </span>
          <span v-if="badge2" class="flex items-center space-x-1">
            <img src="../assets/svgs/Experience.svg" alt="experience" class="w-3 h-3" />
            <span class="font-medium">{{ badge2 }}</span>
          </span>
        </div>

        <!-- Specialization -->
        <div v-if="highlightedText" class="flex items-center mt-2 text-[#222E39] text-xs gap-x-2">
          <span class="font-medium text-[#222E39]">{{ label }}:</span>
          <span class="text-blue-500 font-medium">{{ highlightedText }}</span>
        </div>
      </div>
    </div>

    <!-- Location & Distance -->
    <div v-if="locationText || distanceValue"
      class="bg-gray-50 rounded-md p-2 flex items-center border border-gray-200 shadow-sm">
      <!-- Distance Box -->
      <div v-if="distanceValue"
        class="bg-gray-200 px-3 py-1 rounded-md shadow-inner text-[#222E39] font-semibold text-xs flex flex-col items-center w-16">
        <span class="text-sm font-bold text-[#222E39]">{{ distanceValue }}KM</span>
        <span class="text-[#222E39] text-[10px] font-medium">Away</span>
      </div>

      <!-- Location Information -->
      <div v-if="locationText" class="ml-3 flex flex-col">
        <p class="text-[#222E39] text-xs font-medium">Location:</p>
        <p class="text-[#222E39] text-xs md:text-sm font-medium">{{ truncatedLocation }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, defineProps } from 'vue';

const props = defineProps({
  title: String,
  imageSrc: String,
  isVerified: Boolean,
  ratingValue: Number,
  badge1: String,
  badge2: String,
  label: String,
  highlightedText: String,
  distanceValue: Number,
  locationText: String,
});

const truncatedLocation = computed(() => {
  return props.locationText && props.locationText.length > 40
    ? props.locationText.substring(0, 30) + '...'
    : props.locationText;
});
</script>
