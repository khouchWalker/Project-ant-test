<!-- <script setup lang="ts">
import { ref } from "vue";
import { Icon } from "@iconify/vue";

interface CustomerInfo {
  status: string;
  customerId: string;
  gender: string;
  dateOfBirth: string;
  email: string;
  phoneNumber: string;
  address: string;
  createdDate: string;
}

const card: Ref<CustomerInfo[]> = ref([
  {
    status: "Active",
    customerId: "000035474",
    gender: "Female",
    dateOfBirth: "01 Apr 1990",
    email: "vafgot@vultukir.org",
    phoneNumber: "(123) 456-7890",
    address: "1928 Phnom Penh, 12105",
    createdDate: "01 Apr 1990",
  },
]);

function getStatusColor(status: string): string {
  return status === "Active" ? "green" : "red"; // Customize this based on the status
}
</script>
<template>
  <a-card
    v-for="(customer, index) in card"
    :bodyStyle="{ padding: '24px', height: ' 346px ' }"
    :key="index"
  >
    <a-typography>
      <span class="text-[#4B465C] font-[13px]"> Details</span>
    </a-typography>
    <a-flex class="flex-col">
      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]"> Status: </span>
        <span :style="{ color: getStatusColor(customer.status) }">{{
          customer.status
        }}</span>
      </a-typography>

      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]">Customer ID:</span>
        {{ customer.customerId }}
      </a-typography>

      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]"> Gender: </span>
        {{ customer.gender }}
      </a-typography>

      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]">
          Date of Birth:
        </span>
        {{ customer.dateOfBirth }}
      </a-typography>

      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]"> Email: </span>
        {{ customer.email }}
      </a-typography>

      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]">
          Phone Number:
        </span>
        {{ customer.phoneNumber }}
      </a-typography>

      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]"> Address: </span>
        {{ customer.address }}
      </a-typography>

      <a-typography>
        <span class="text-sm font-semibold text-[#4B465C]">
          Created Date:
        </span>
        {{ customer.createdDate }}
      </a-typography>
    </a-flex>
  </a-card>
</template>
<style scoped></style> -->
<script setup lang="ts">
import { ref } from "vue";
import { Icon } from "@iconify/vue";

interface CustomerInfo {
  status: string;
  customerId: string;
  gender: string;
  dateOfBirth: string;
  email: string;
  phoneNumber: string;
  address: string;
  createdDate: string;
}

const card: Ref<CustomerInfo[]> = ref([
  {
    status: "Active",
    customerId: "000035474",
    gender: "Female",
    dateOfBirth: "01 Apr 1990",
    email: "vafgot@vultukir.org",
    phoneNumber: "(123) 456-7890",
    address: "1928 Phnom Penh, 12105",
    createdDate: "01 Apr 1990",
  },
]);

const cardText = {
  detailsTitle: "Details",
  statusLabel: "Status",
  customerIdLabel: "Customer ID",
  genderLabel: "Gender",
  dobLabel: "Date of Birth",
  emailLabel: "Email",
  phoneNumberLabel: "Phone Number",
  addressLabel: "Address",
  createdDateLabel: "Created Date",
};

function getStatusColor(status: string): string {
  return status === "Active" ? "green" : "red"; // Customize this based on the status
}
</script>
<template>
  <a-card
    v-for="(customer, index) in card"
    :bodyStyle="{ padding: '24px' }"
    :key="index"
  >
    <a-row :gutter="10">
      <a-col :span="24">
        <span class="text-[#4B465C] font-[13px]">{{
          cardText.detailsTitle
        }}</span>
      </a-col>
      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.statusLabel }}:
        </span>

        <span :style="{ color: getStatusColor(customer.status) }" class="pl-2">
          {{ customer.status }}
        </span>
      </a-col>

      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.customerIdLabel }}:
        </span>
        {{ customer.customerId }}
      </a-col>

      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.genderLabel }}:
        </span>
        {{ customer.gender }}
      </a-col>

      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.dobLabel }}:
        </span>
        {{ customer.dateOfBirth }}
      </a-col>

      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.emailLabel }}:
        </span>
        {{ customer.email }}
      </a-col>

      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.phoneNumberLabel }}:
        </span>
        {{ customer.phoneNumber }}
      </a-col>

      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.addressLabel }}:
        </span>
        {{ customer.address }}
      </a-col>

      <a-col :span="24">
        <span class="text-sm font-semibold text-[#4B465C]">
          {{ cardText.createdDateLabel }}:
        </span>
        {{ customer.createdDate }}
      </a-col>
    </a-row>
  </a-card>
</template>

<style scoped></style>
