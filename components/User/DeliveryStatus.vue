<script setup lang="ts">
import { Icon } from "@iconify/vue";

const status = ref([
  {
    icon: "tabler:truck-delivery",
    sell: "230k",
    total: "On Delivery",
    bgColor: "#00BAD129",
    color: "#00BAD1",
  },

  {
    icon: "tabler:shopping-cart",
    sell: " 8.549k ",
    total: "Completed ",
    bgColor: "#00BAD129",
    color: "#00BAD1 ",
  },
  {
    icon: "tabler:truck-off",
    sell: "1,222",
    total: "Canceled",
    bgColor: "#FF4C5129",
    color: "#FF4C51",
  },
  {
    icon: "tabler:truck-return",
    sell: "1,222",
    total: "Return",
    bgColor: "#FF9F4314",
    color: "#E68F3C ",
  },
  {
    icon: "tabler:report-money",
    sell: "$9745",
    total: "Refunded",
    bgColor: "#28C76F29",
    color: "#28C76F",
  },
]);
</script>
<template>
  <a-row>
    <a-card
      class="h-auto w-full"
      :bodyStyle="{ padding: '24px 24px 0px 24px' }"
    >
      <a-flex class="justify-between">
        <a-typography-text class="font-sans text-xl font-medium"
          >Delivery Statistics</a-typography-text
        >
        <a-flex class="flex">
          <a-typography-text class="m-auto"
            >Updated 1 month ago</a-typography-text
          >
        </a-flex>
      </a-flex>
      <a-row class="justify-between">
        <a-col
          v-for="(st, index) in status"
          :key="index"
          class="flex gap-1 py-5"
          :xs="12"
          :sm="12"
          :md="12"
          :lg="6"
          :xl="4"
        >
          <a-flex
            class="flex h-10 w-10 rounded-md mt-1"
            :style="{ background: st.bgColor }"
          >
            <Icon
              :icon="st.icon"
              :style="{ color: st.color }"
              class="w-5 h-5 m-auto icon"
            />
          </a-flex>
          <a-flex class="flex-col">
            <a-typography-text class="text-lg font-medium">{{
              st.sell
            }}</a-typography-text>
            <a-typography-text class="text-[#2F2B3DB2] text-sm">{{
              st.total
            }}</a-typography-text>
          </a-flex>
        </a-col>
      </a-row>
    </a-card>
  </a-row>
</template>
<!-- <script setup lang="ts">
import { Icon } from "@iconify/vue";
</script>
<template>
  <a-col>
    <a-card class="w-full">
      <a-flex vertical gap="0">
        <a-row class="mb-1 justify-between">
          <a-typography-text
            class="text-lg font-medium"
            style="color: #2f2b3de5"
            >Delivery Statistics</a-typography-text
          >
          <a-typography-text
            class="text-lg font-medium"
            style="color: #2f2b3de5"
            >Updated 1 month ago</a-typography-text
          >
        </a-row>
        <a-row :gutter="0">
          <a-col :flex="2">
            <a-flex align="center" gap="20" class="w-44" justify="flex-start">
              <a-avatar
                shape="square"
                :size="40"
                style="
                  background-color: #005c9433;
                  display: flex;
                  align-items: center;
                "
              >
                <Icon
                  icon="tabler:truck-delivery"
                  width="24"
                  height="24"
                  style="color: #005c94"
                />
              </a-avatar>
              <a-flex vertical>
                <a-typography-text
                  class="text-lg font-medium"
                  style="color: #2f2b3de5"
                  >9K</a-typography-text
                >
                <a-typography-text
                  class="font-normal text-sm"
                  style="color: #2f2b3db2"
                  >On Delivery</a-typography-text
                >
              </a-flex>
            </a-flex>
          </a-col>
          <a-col :flex="2">
            <a-flex align="center" gap="20" class="w-44" justify="flex-start">
              <a-avatar
                shape="square"
                :size="40"
                style="
                  background-color: #00bad129;
                  display: flex;
                  align-items: center;
                "
              >
                <Icon
                  icon="tabler:shopping-cart"
                  width="24"
                  height="24"
                  style="color: #00bad1"
                />
              </a-avatar>
              <a-flex vertical>
                <a-typography-text
                  class="text-lg font-medium"
                  style="color: #2f2b3de5"
                  >8.549k</a-typography-text
                >
                <a-typography-text
                  class="font-normal text-sm"
                  style="color: #2f2b3db2"
                  >Completed</a-typography-text
                >
              </a-flex>
            </a-flex>
          </a-col>
          <a-col :flex="2">
            <a-flex align="center" gap="20" class="w-44" justify="flex-start">
              <a-avatar
                shape="square"
                :size="40"
                style="
                  background-color: #ff4c5129;
                  display: flex;
                  align-items: center;
                "
              >
                <Icon
                  icon="tabler:truck-off"
                  width="24"
                  height="24"
                  style="color: #ff4c51"
                />
              </a-avatar>
              <a-flex vertical>
                <a-typography-text
                  class="text-lg font-medium"
                  style="color: #2f2b3de5"
                  >1,222</a-typography-text
                >
                <a-typography-text
                  class="font-normal text-sm"
                  style="color: #2f2b3db2"
                  >Canceled</a-typography-text
                >
              </a-flex>
            </a-flex>
          </a-col>
          <a-col :flex="2">
            <a-flex align="center" gap="20" class="w-44" justify="flex-start">
              <a-avatar
                shape="square"
                :size="40"
                style="
                  background-color: #ff9f4314;
                  display: flex;
                  align-items: center;
                "
              >
                <Icon
                  icon="tabler:truck-return"
                  width="24"
                  height="24"
                  style="color: #e68f3c"
                />
              </a-avatar>
              <a-flex vertical>
                <a-typography-text
                  class="text-lg font-medium"
                  style="color: #2f2b3de5"
                  >1,222</a-typography-text
                >
                <a-typography-text
                  class="font-normal text-sm"
                  style="color: #2f2b3db2"
                  >Return</a-typography-text
                >
              </a-flex>
            </a-flex>
          </a-col>
          <a-col :flex="2">
            <a-flex align="center" gap="20" class="w-44" justify="flex-start">
              <a-avatar
                shape="square"
                :size="40"
                style="
                  background-color: #28c76f29;
                  display: flex;
                  align-items: center;
                "
              >
                <Icon
                  icon="tabler:report-money"
                  width="24"
                  height="24"
                  style="color: #28c76f"
                />
              </a-avatar>
              <a-flex vertical>
                <a-typography-text
                  class="text-lg font-medium"
                  style="color: #2f2b3de5"
                  >$9745</a-typography-text
                >
                <a-typography-text
                  class="font-normal text-sm"
                  style="color: #2f2b3db2"
                  >Refunded</a-typography-text
                >
              </a-flex>
            </a-flex>
          </a-col>
        </a-row>
      </a-flex>
    </a-card>
  </a-col>
</template> -->
