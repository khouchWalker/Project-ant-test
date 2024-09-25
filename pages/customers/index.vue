<script setup lang="ts">
definePageMeta({
  layout: "dashboard",
});
</script>

<template>
  <a-row :gutter="20">
    <a-col :xs="24" :sm="24" :md="24" :lg="24" :xl="6" :xxl="6" class="py-2">
      <CustomerInfoCustumerAdd />
    </a-col>
    <a-col :xs="24" :sm="24" :md="24" :lg="24" :xl="18" :xxl="18" class="py-2">
      <CustomerInfoData />
    </a-col>

    <a-col :span="24" class="pt-3">
      <TableInfo />
    </a-col>
  </a-row>
</template>

<style scoped></style>
