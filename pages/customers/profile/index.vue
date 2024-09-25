<script setup lang="ts">
definePageMeta({
  layout: "dashboard",
});
</script>

<template>
  <a-row :gutter="20">
    <a-col :xs="24" :sm="24" :md="24" :lg="24" :xl="7" :xxl="6" class="py-2">
      <UserProfile />
    </a-col>
    <a-col :xs="24" :sm="24" :md="24" :lg="24" :xl="17" :xxl="18" class="py-2">
      <UserDeliveryStatus />
    </a-col>

    <a-col :span="24">
      <ProfileStatus />
    </a-col>
  </a-row>
</template>

<style scoped></style>
