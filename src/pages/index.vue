<template>
  <div v-if="current_profile === 1" :key="'profile-user'">
    <MyProfile />
  </div>
  <div v-else :key="'profile-pharmacist'">
    <MyProfilePharmacist />
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  import MyProfilePharmacist from '@/components/MyProfilePharmacist.vue';
  import MyProfile from '@/components/MyProfile.vue';

  const current_profile = ref(2);
</script>
