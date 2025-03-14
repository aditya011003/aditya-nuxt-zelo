<template>
    <div class="min-h-screen flex items-center justify-center bg-gray-50 p-6">
      <CardComponent
        :name="'Andrew Chapman'"
        :profileImage="'/path-to-image.jpg'"
        :verified="true"
        :rating="450"
        :qualification="'MD'"
        :experience="12"
        :specialization="'Family Medicine'"
        :distance="8"
        :location="'4140 Parker Rd. Allentown, New Mexico 31134'"
      />
    </div>
  </template>
  
  <script>
  import CardComponent from '~/components/CardComponent.vue';
  
  export default {
    components: {
      CardComponent,
    },
  };
  </script>
  