<template>
  <div class="flex flex-col w-full min-h-screen">
    <!-- Page Header at the Top -->
    <PageHeader
      :headerTitle="headerTitle"
      :actionButtons="actionButtons"
      :showBackButton="showBackButton"
      :onBack="onBack"
    />

    <div class="flex flex-1 mt-6 px-6">
      <!-- Left Sidebar: Sticky Profile Card -->
      <div class="w-80 sticky top-5 h-max">
        <StickyProfileCard
          :imageSrc="profileData.profileImage"
          :displayName="profileData.name"
          :isVerified="true"
          :verificationIcon="verfiedBadge"
          :verificationText="'Verified Provider'"
          :ratingValue="profileData.rating"
          :totalReviews="profileData.reviews"
          :specializationLabel="'Primary Specialization:'"
          :specializationValue="profileData.specialization"
          :badgeOne="profileData.degree"
          :badgeOneIcon="education"
          :badgeTwo="profileData.experience"
          :badgeTwoIcon="experiance"
          :badgeThree="profileData.distance"
          :badgeThreeIcon="Distance"
          :statOneLabel="'Specialties'"
          :statOneValue="profileData.specialties"
          :statTwoLabel="'Hospitals'"
          :statTwoValue="profileData.hospitals"
          :locationLabel="'Location:'"
          :locationValue="profileData.address"
          :contactInfo="profileData.phone"
          :buttonText="'Add a Review'"
          :handleButtonClick="onReviewClick"
        />
      </div>

      <!-- Main Content Area -->
      <div class="flex-1 ml-6">
        <RankingComponent :rankings="rankingData" />
        <slot></slot>
        <!-- For dynamic content (other components) -->
         <div class="mt-4">
        <MapInfoSection
        :mapTitle="'Map Location'"
        :mapSrc="'https://www.google.com/maps/embed?...'"
        :infoSections="[
          {
            title: 'Qualification',
            icon: '../assets/svgs/education.svg',
            description: 'MD - University of Oxford Medical School, 1999',
          },
          {
            title: 'Facility Types',
            items: [
              'Telehealth Services Provided',
              '2+ Affiliated Hospitals',
              '5+ Specialties',
            ],
          },
          {
            title: 'Specialties',
            items: ['Family Medicine', 'Pediatrics', 'Dermatologist'],
          },
        ]"
      />
    </div>

    <!-- ✅ Matrices Section (Placed Below Map Info Section) -->
    <!-- <MatricesSection /> -->
    <ProcedureMetrics />

      </div>
      
    </div>
  </div>
</template>

<script setup>
import PageHeader from "@/components/PageHeader.vue";
import StickyProfileCard from "@/components/StickyProfileCard.vue";
import education from "../assets/svgs/Education.svg";
import experiance from "../assets/svgs/Experience.svg";
import Distance from "../assets/svgs/Distance.svg";
import State_Ranking from "../assets/svgs/state-ranking.svg";
import National_Ranking from "../assets/svgs/national-ranking.svg";
import Dislike from "../assets/svgs/Dislike.svg";
import verfiedBadge from "../assets/svgs/verifiedBadge.svg";
import { defineProps } from "vue";
import RankingComponent from "./RankingComponent.vue";
import MapInfoSection from "./MapInfoSection.vue";
import MatricesSection from "./MatricesSection.vue";

defineProps({
  headerTitle: String,
  actionButtons: Array,
  showBackButton: {
    type: Boolean,
    default: true,
  },
  onBack: Function,
  profileData: Object,
  onReviewClick: Function,
});
const rankingData = [
  {
    state: {
      icon: State_Ranking,
      description: "In 13 Adult Specialties, In 4 Children’s Specialties",
    },
    national: {
      icon: National_Ranking,
      description: "In 13 Adult Specialties, In 4 Children’s Specialties",
    },
  },
  {
    state: {
      icon: State_Ranking,
      description: "In 10 Adult Specialties, In 3 Children’s Specialties",
    },
    national: {
      icon: National_Ranking,
      description: "In 15 Adult Specialties, In 5 Children’s Specialties",
    },
  },
];
</script>
