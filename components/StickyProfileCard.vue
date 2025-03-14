<template>
  <div class="bg-white shadow-lg rounded-2xl p-5 w-full max-w-xs sticky top-5">
    <!-- Profile Image -->
    <div class="flex flex-col items-center text-[#222E39]">
      <div class="w-24 h-24 rounded-xl shadow-md overflow-hidden mb-3">
        <img :src="imageSrc" alt="Profile" class="w-full h-full object-cover" />
      </div>

      <!-- Name and Verification -->
      <div class="flex items-center space-x-2">
        <h2 class="text-lg font-semibold">{{ displayName }}</h2>
      </div>

      <!-- Additional Details -->
      <div class="flex items-center space-x-4 mt-2 text-sm text-gray-600">
        <!-- First Badge -->
        <div class="flex items-center space-x-1">
          <img :src="badgeOneIcon" alt="Badge One" class="w-4 h-4" />
          <span>{{ badgeOne }}</span>
        </div>
        <div class="w-[1px] h-4 bg-gray-300 rotate-180"></div>

        <!-- Second Badge -->
        <div class="flex items-center space-x-1">
          <img :src="badgeTwoIcon" alt="Badge Two" class="w-4 h-4" />
          <span>{{ badgeTwo }}</span>
        </div>
        <div class="w-[1px] h-4 bg-gray-300 rotate-180"></div>

        <!-- Third Badge -->
        <div class="flex items-center space-x-1">
          <img :src="badgeThreeIcon" alt="Badge Three" class="w-4 h-4" />
          <span>{{ badgeThree }}</span>
        </div>
      </div>

      <!-- Verification Badge -->
      <div
        v-if="isVerified"
        class="flex items-center mt-2 space-x-2 text-blue-500 font-semibold"
      >
        <img :src="verificationIcon" alt="Verified" class="w-5 h-5" />
        <span>{{ verificationText }}</span>
      </div>

      <!-- Ratings -->
      <div class="flex items-center mt-2">
        <div class="flex text-yellow-400 text-xl">
          <span
            v-for="star in 5"
            :key="star"
            :class="star <= ratingValue ? 'text-yellow-400' : 'text-gray-300'"
          >
            ★
          </span>
        </div>
        <span class="text-sm text-gray-600 ml-2">({{ totalReviews }})</span>
      </div>
    </div>

    <!-- Specialization -->
    <div class="mt-4 text-center flex flex-row items-center justify-between">
      <p class="text-sm text-gray-600">{{ specializationLabel }}</p>
      <p class="text-blue-500 font-semibold">{{ specializationValue }}</p>
    </div>

    <!-- Specialties and Hospitals -->
    <div
      class="flex items-center justify-center bg-white rounded-xl shadow-md mt-2 p-4 border border-gray-200"
    >
      <div class="flex-1 text-center">
        <p class="text-xl font-bold text-[#222E39]">{{ statOneValue }}</p>
        <p class="text-sm text-gray-500">{{ statOneLabel }}</p>
      </div>

      <div class="w-[1.5px] h-10 bg-gray-300 rotate-12"></div>

      <div class="flex-1 text-center">
        <p class="text-xl font-bold text-[#222E39]">{{ statTwoValue }}</p>
        <p class="text-sm text-gray-500">{{ statTwoLabel }}</p>
      </div>
    </div>

    <!-- Location and Distance -->
    <div class="bg-gray-100 rounded-lg p-3 mt-4">
      <div class="ml-3">
        <p class="text-gray-500 text-xs">{{ locationLabel }}</p>
        <p class="text-gray-800 text-sm font-medium">
          {{ locationValue }}
        </p>
      </div>
    </div>

    <!-- Review Button -->
    <button
      @click="handleButtonClick"
      class="bg-yellow-400 text-white w-full py-2 mt-4 rounded-lg font-semibold"
    >
      {{ buttonText }}
    </button>

    <!-- Contact -->
    <div
      class="flex items-center justify-center bg-white rounded-xl shadow-md border border-gray-200 mt-4 p-3"
    >
      <!-- Phone Icon -->
      <img src="../assets/svgs/Call.svg" alt="Phone" class="w-5 h-5 mr-2" />

      <!-- Phone Number -->
      <span class="text-[#222E39] font-semibold text-base">{{
        contactInfo
      }}</span>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps({
  imageSrc: String,
  displayName: String,
  isVerified: Boolean,
  verificationIcon: String,
  verificationText: String,
  ratingValue: Number,
  totalReviews: Number,
  specializationLabel: String,
  specializationValue: String,
  badgeOne: String,
  badgeOneIcon: String,
  badgeTwo: String,
  badgeTwoIcon: String,
  badgeThree: String,
  badgeThreeIcon: String,
  statOneLabel: String,
  statOneValue: Number,
  statTwoLabel: String,
  statTwoValue: Number,
  locationLabel: String,
  locationValue: String,
  contactInfo: String,
  buttonText: String,
  handleButtonClick: Function,
});
</script>
