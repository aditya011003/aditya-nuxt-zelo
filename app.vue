<template>
  <PageLayout
    headerTitle="Provider's Details"
    :actionButtons="[
      { label: 'Share', icon: Call, onClick: () => console.log('Share Clicked') },
      { label: 'Give Endorse', icon: Like, bgColor: 'bg-blue-600 text-white', onClick: () => console.log('Endorse Clicked') },
      { label: 'Disapprove', icon: Dislike, bgColor: 'bg-red-500 text-white', onClick: () => console.log('Disapprove Clicked') }
    ]"
    :profileData="{
      profileImage: profileImg,
      name: 'Andrew Chapman',
      specialization: 'Family Medicine',
      rating: 4.5,
      reviews: 450,
      experience: '12 Years',
      degree: 'MD',
      distance: '8 KM',
      address: '440 Parker Rd. Allentown, New Mexico 31134',
      specialties: 25,
      hospitals: 2590,
      phone: '(270) 555-0117'
    }"
    :onReviewClick="() => console.log('Review Clicked')"
  >    
  </PageLayout>
</template>

<script setup>
import { Link } from "#components";
import Like from "./assets/svgs/Like.svg";
import Dislike from "./assets/svgs/Dislike.svg";
import Call from "./assets/svgs/Call.svg";
import profileImg from "./assets/svgs/avatar-1.svg";
import PageLayout from "@/components/PageLayout.vue";
</script>
