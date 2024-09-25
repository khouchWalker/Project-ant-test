<script setup lang="ts">
import { Icon } from "@iconify/vue";
const data = ref([
  {
    title: " New Customer",
    number: 860,
    total: "Total Today",
    Icon: "lucide:user-plus",
    bgColor: "#EA545514",
    Color: "#28C76F",
  },
]);
// const status = ref([
//   {
//     icon: "tabler:building-store",
//     sell: "9K",
//     total: "Total Today",
//     bgColor: "#00BAD129 ",
//     color: "#2F2B3DE5",
//   },

//   {
//     icon: "tabler:golf",
//     sell: " 97 ",
//     total: "Customer KYS ",
//     bgColor: "#28C76F29",
//     color: "#28C76F",
//   },
//   {
//     icon: "tabler:activity",
//     sell: "423",
//     total: "Active",
//     bgColor: "#FF4C5129",
//     color: "#2F2B3DE5",
//   },
//   {
//     icon: "tabler:radioactive",
//     sell: "230",
//     total: "Inactive",
//     bgColor: "#005C9433",
//     color: "#2F2B3DE5",
//   },
// ]);
</script>
<template>
  <a-card v-for="(datas, index) in data" :key="index" class="h-auto">
    <a-flex class="gap-5 p-4">
      <a-flex class="flex-col">
        <a-typography>{{ datas.title }}</a-typography>
        <a-typography class="text-xl">{{ datas.number }}</a-typography>
        <a-typography>{{ datas.total }}</a-typography>
      </a-flex>
      <a-flex
        class="h-7 w-7 flex rounded-sm"
        :style="{ background: datas.bgColor }"
      >
        <Icon
          :icon="datas.Icon"
          class="w-5 h-5 m-auto"
          :style="{ color: datas.Color }"
        />
      </a-flex>
    </a-flex>
  </a-card>
</template>
