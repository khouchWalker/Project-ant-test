<script setup lang="ts">
// definePageMeta({
//   layout: "dashboard",
// });
</script>

<template>
  <a-row :gutter="20">
    <a-col :xs="24" :sm="24" :md="24" :lg="24" :xl="7" :xxl="6" class="py-2">
      <ProfileUserUserDetailLoginDetail />
    </a-col>
    <a-col :xs="24" :sm="24" :md="24" :lg="24" :xl="17" :xxl="18" class="py-2">
      <a-row class="pb-4">
        <ProfileUserUserDetailTwoFactor />
      </a-row>
      <a-row>
        <ProfileUserUserDetailLogin />
      </a-row>
    </a-col>
  </a-row>
</template>

<style scoped></style>
