<template>
    <div class="flex justify-between items-center bg-white rounded-lg p-4 w-full">
      <!-- Left Section: Back Arrow & Title -->
      <div class="flex items-center space-x-4">
        <!-- Back Button -->
        <button v-if="showBackButton" @click="onBack" class="w-10 h-10 bg-white rounded-lg flex items-center justify-center">
          <img src="../assets/svgs/Arrow.svg" alt="Back" class="w-6 h-6" />
        </button>
  
        <!-- Title -->
        <h1 class="text-xl font-semibold text-[#222E39]">{{ headerTitle }}</h1>
      </div>
  
      <!-- Right Section: CTA Buttons -->
      <div class="flex items-center space-x-4">
        <button
          v-for="(button, index) in actionButtons"
          :key="index"
          @click="button.onClick"
          :class="[
            'flex items-center space-x-2 rounded-lg px-4 py-2 font-semibold',
            button.bgColor || 'bg-white border border-gray-300 text-gray-600',
            button.textColor || ''
          ]"
        >
          <img :src="button.icon" :alt="button.label" class="w-5 h-5" v-if="button.icon" />
          <span>{{ button.label }}</span>
        </button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from "vue";
  
  defineProps({
    headerTitle: {
      type: String,
      required: true
    },
    showBackButton: {
      type: Boolean,
      default: true
    },
    backIcon: {
      type: String,
      default: "../assets/svgs/Arrow.svg"
    },
    onBack: {
      type: Function,
      default: () => console.log("Back button clicked")
    },
    actionButtons: {
      type: Array,
      default: () => []
    }
  });
  </script>
  