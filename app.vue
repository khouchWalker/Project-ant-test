<script setup lang="ts"></script>
<template>
  <a-extract-style>
    <a-config-provider
      :theme="{
        token: {
          colorPrimary: '#005C94',
          // fontFamily: 'Noto Sans',
          colorInfo: '#005C94',
          colorLink: '#005C94',
          colorText: '#4B465C',
        },
        components: {
          Form: {
            colorTextHeading: '#4B465C',
          },
        },
      }"
    >
      <NuxtLayout>
        <NuxtPage />
      </NuxtLayout>
    </a-config-provider>
  </a-extract-style>
</template>
