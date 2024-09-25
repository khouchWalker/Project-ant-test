<script setup lang="ts">
import { Icon } from "@iconify/vue";
// const data = ref([
//   {
//     title: " New Customer",
//     number: 860,
//     total: "Total Today",
//     Icon: "lucide:user-plus",
//   },
// ]);
const status = ref([
  {
    icon: "tabler:building-store",
    sell: "9K",
    total: "Total Today",
    bgColor: "#00BAD129 ",
    color: "#2F2B3DE5",
  },

  {
    icon: "tabler:golf",
    sell: " 97 ",
    total: "Customer KYS ",
    bgColor: "#28C76F29",
    color: "#28C76F",
  },
  {
    icon: "tabler:activity",
    sell: "423",
    total: "Active",
    bgColor: "#FF4C5129",
    color: "#2F2B3DE5",
  },
  {
    icon: "tabler:radioactive",
    sell: "230",
    total: "Inactive",
    bgColor: "#005C9433",
    color: "#2F2B3DE5",
  },
]);
// const isMobile = ref(window.innerWidth <= 768);
// window.addEventListener("resize", () => {
//   isMobile.value = window.innerWidth <= 768;
// :justify="isMobile ? 'center' : 'start'"
// });
</script>
<template>
  <a-row :span="24">
    <a-card class="h-auto w-full">
      <a-row>
        <a-col :span="14">
          <a-typography class="font-sans text-3xl">Statistic</a-typography>
        </a-col>
        <a-col :span="10">
          <a-flex class="justify-end">
            <a-typography class="py-2">
              Real Time Update : 2023-09-02, 11:00 AM
            </a-typography>
          </a-flex>
        </a-col>
      </a-row>
      <a-row class="pt-4">
        <a-col
          :xs="12"
          :sm="12"
          :md="12"
          :lg="12"
          :xl="6"
          v-for="(st, index) in status"
          :key="index"
          class="flex gap-2"
        >
          <a-flex
            class="h-10 w-10 rounded-md mt-1"
            :style="{ background: st.bgColor }"
          >
            <Icon
              :icon="st.icon"
              class="w-5 h-5 m-auto"
              :style="{ color: st.color }"
            />
          </a-flex>
          <a-flex class="flex-col">
            <a-typography class="text-lg font-medium">{{
              st.sell
            }}</a-typography>
            <a-typography>{{ st.total }}</a-typography>
          </a-flex>
        </a-col>
      </a-row>
    </a-card>
  </a-row>
</template>

<style scoped></style>
