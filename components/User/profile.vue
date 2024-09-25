<script setup lang="ts">
import { Icon } from "@iconify/vue";
const data = ref([
  {
    title: " Violet Mendoza",

    total: " Kiritoyuki7776",
  },
]);
</script>
<template>
  <a-row :span="4">
    <a-card v-for="(datas, index) in data" :key="index" class="h-36 w-full">
      <a-flex>
        <a-avata class="bg-red-100 h-24 w-24 flex rounded-sm mt-1">
          <img src="/assets/images/Avatar (2).jpg" alt="" />
        </a-avata>
        <a-flex class="flex-col self-center">
          <a-typography-text class="font-medium mb-2">{{
            datas.title
          }}</a-typography-text>
          <a-badge class="bg-[#A8AAAE29] rounded-md p-1 m-auto flex">
            <a-typography class="flex text-[#A8AAAE] text-xs self-center">{{
              datas.total
            }}</a-typography>
          </a-badge>
        </a-flex>
      </a-flex>
    </a-card>
  </a-row>
</template>
