<script setup lang="ts">
import { ref } from "vue";
import { Icon } from "@iconify/vue";

const columns = [
  {
    title: "BROWSER",
    dataIndex: "browser",
    key: "browser",
  },
  {
    title: "DEVICE",
    dataIndex: "device",
    key: "device",
  },
  {
    title: "LOCATION",
    dataIndex: "location",
    key: "location",
  },
];

const data = [
  {
    key: "1",
    browser: {
      name: "Chrome on Windows",
      icon: "tabler:brand-windows",
      color: "#00BAD1",
    },
    device: "Dell XPS 15",
    location: "New York, NY",
  },
  {
    key: "2",
    browser: {
      name: "Chrome on Android",
      icon: "tabler:brand-android",
      color: "#34A853",
    },
    device: "Google Pixel 3a",
    location: "Los Angeles, CA",
  },
  {
    key: "3",
    browser: {
      name: "Chrome on iPhone",
      icon: "tabler:brand-apple",
      color: "#F56A00",
    },
    device: "iPhone 12x",
    location: "San Francisco, CA",
  },
  {
    key: "4",
    browser: {
      name: "Chrome on MacOS",
      icon: "tabler:brand-apple",
      color: "#999999",
    },
    device: "Apple iMac",
    location: "New York, NY",
  },
  {
    key: "5",
    browser: {
      name: "Chrome on MacOS",
      icon: "tabler:brand-apple",
      color: "#007AFF",
    },
    device: "MacBook Pro",
    location: "Los Angeles, CA",
  },
  {
    key: "6",
    browser: {
      name: "Chrome on Android",
      icon: "tabler:brand-android",
      color: "#FF5722",
    },
    device: "OnePlus 9 Pro",
    location: "San Francisco, CA",
  },
];

// interface CustomerInfo {
//   status: string;
//   customerId: string;
//   gender: string;
//   dateOfBirth: string;
//   email: string;
//   phoneNumber: string;
//   address: string;
//   createdDate: string;
// }

// const card: Ref<CustomerInfo[]> = ref([
//   {
//     status: "Active",
//     customerId: "000035474",
//     gender: "Female",
//     dateOfBirth: "01 Apr 1990",
//     email: "vafgot@vultukir.org",
//     phoneNumber: "(123) 456-7890",
//     address: "1928 Phnom Penh, 12105",
//     createdDate: "01 Apr 1990",
//   },
// ]);

function getStatusColor(status: string): string {
  return status === "Active" ? "green" : "red";
}
</script>
<template>
  <a-card class="w-full">
    <a-typography class="font-medium text-xl mb-4">
      Recent Devices
    </a-typography>
    <a-table
      :columns="columns"
      :dataSource="data"
      :pagination="false"
      :scroll="{ x: ' max-content' }"
    >
      <template #bodyCell="{ column, text }">
        <div v-if="column.dataIndex === 'browser'" class="flex items-center">
          <Icon :icon="text.icon" :color="text.color" class="mr-2" />
          <span class="font-medium text-base">
            {{ text.name }}
          </span>
        </div>
      </template>
    </a-table>
  </a-card>
</template>
<style scoped>
a-typography {
  font-size: 26px; /* Example of custom font size */
  color: #333; /* Example of custom color */
}
</style>
