<script lang="ts" setup>
import { Icon } from "@iconify/vue";
// import Index from "../Sidebar/index.vue";

const columns = [
  {
    title: " Customer ",
    dataIndex: "name",
    // sorter: (a: DataItem, b: DataItem) => a.name.localeCompare(b.name),
  },
  {
    title: "SEX",
    dataIndex: "SEX",
    sorter: (a: DataItem, b: DataItem) => a.status.localeCompare(b.status),
  },
  {
    title: "Created Date",
    dataIndex: "created_date",
    sorter: (a: DataItem, b: DataItem) =>
      a.created_date.localeCompare(b.created_date),
  },
  // {
  //   title: "Subscription",
  //   dataIndex: "subscription",
  //   sorter: (a: DataItem, b: DataItem) =>
  //     a.subscription.localeCompare(b.subscription),
  // },
  {
    title: "Order",
    dataIndex: "order",
    sorter: (a: DataItem, b: DataItem) => a.kyc.localeCompare(b.kyc),
  },

  {
    title: "ACTIONS",
    dataIndex: "actions",
  },
];

// type Key = string | number;

// enum kycStatus {
//   In_review = "In review",
//   No = "No",
//   Yes = "Yes",
// }

// enum ProductStatus {
//   Active = "Active",
//   Inactive = "Inactive",
//   Re_New = "Re New",
//   Suspended = "Suspended",
// }

interface DataItem {
  key: Key;
  name: string;

  created_date: string;
  // subscription: string;
  Order: number;

  active: boolean;
  Username: string;
  timne: string;
  date: string;
}

const data: Ref<DataItem[]> = ref([
  {
    key: 1,
    name: "Jordan Stevenson",
    // subscription: "Plan Name",
    created_date: "09 May 2022",
    Order: 23,
    status: "Female",
    username: "username",
    time: "11:00 PM",
    date: "Renew on 21 June 2024",
  },
  {
    key: 1,
    name: "Jordan Stevenson",
    // subscription: "Plan Name",
    created_date: "09 May 2022",
    Order: 23,
    status: "Female",
    username: "username",
    time: "11:00 PM",
    date: "Renew on 21 June 2024",
  },
  {
    key: 1,
    name: "Jordan Stevenson",
    // subscription: "Plan Name",
    created_date: "09 May 2022",
    Order: 23,
    status: "Female",
    username: "username",
    time: "11:00 PM",
    date: "Renew on 21 June 2024",
  },
  {
    key: 1,
    name: "Jordan Stevenson",
    // subscription: "Plan Name",
    created_date: "09 May 2022",
    Order: 23,
    status: "Female",
    username: "username",
    time: "11:00 PM",
    date: "Renew on 21 June 2024",
  },
  {
    key: 1,
    name: "Jordan Stevenson",
    // subscription: "Plan Name",
    created_date: "09 May 2022",
    Order: 23,
    status: "Female",
    username: "username",
    time: "11:00 PM",
    date: "Renew on 21 June 2024",
  },
  {
    key: 1,
    name: "Jordan Stevenson",
    // subscription: "Plan Name",
    created_date: "09 May 2022",
    Order: 23,
    status: "Female",
    username: "username",
    time: "11:00 PM",
    date: "Renew on 21 June 2024",
  },
]);

const route = ref([
  {
    path: "/customers/profile",
  },
]);

const search = ref("");

// const state = reactive<{
//   selectedRowKeys: Key[];
//   loading: boolean;
// }>({
//   selectedRowKeys: [], // Check here to configure the default column
//   loading: false,
// });

// const onSelectChange = (selectedRowKeys: Key[]) => {
//   console.log("selectedRowKeys changed: ", selectedRowKeys);
//   state.selectedRowKeys = selectedRowKeys;
// };

// function getkycColor(stock: kycStatus) {
//   switch (stock) {
//     case kycStatus.In_review:
//       return "cyan";
//     case kycStatus.No:
//       return "orange";
//     default:
//       return "green";
//   }
// }

// function getStatusColor(status: ProductStatus) {
//   switch (status) {
//     case ProductStatus.Active:
//       return "green";
//     case ProductStatus.Re_New:
//       return "orange";
//     case ProductStatus.Suspended:
//       return "red";
//     default:
//       return "cyan";
//   }
// }
</script>

<template>
  <a-card class="w-full" :body-style="{ padding: '0' }">
    <div class="mb-6 px-5 pt-5">
      <a-typography class="text-3xl pb-4" style="color: #4b465c"
        >All Customer</a-typography
      >
      <a-row :gutter="18">
        <a-col :span="6">
          <a-input class="w-full" placeholder=" Search">
            <template #prefix>
              <Icon icon="tabler:search" class="w-5 h-5" />
            </template>
          </a-input>
        </a-col>
        <a-col :span="6">
          <a-select placeholder=" Customer  KYC" style="width: 100%"></a-select>
        </a-col>
        <a-col :span="6">
          <a-select
            placeholder="Customer Status"
            style="width: 100%"
          ></a-select>
        </a-col>
        <a-col :span="6">
          <a-range-picker v-model:value="date" class="w-full" />
        </a-col>
      </a-row>
    </div>
    <a-divider class="m-0" />
    <a-table
      :columns="columns"
      :data-source="data"
      :scroll="{ x: 'max-content' }"
    >
      <template #bodyCell="{ column, record }">
        <template v-if="column.dataIndex === 'name'">
          <a-space>
            <a-avatar>
              <template #icon>
                <UserOutlined />
              </template>
            </a-avatar>
            <div>
              <a-typography-text
                class="font-normal text-sm"
                style="color: #005c94"
              >
                {{ record.name }}
              </a-typography-text>
              <div>
                <a-typography-text
                  class="text-base font-normal"
                  style="color: #4b465c"
                  >{{ record.username }}</a-typography-text
                >
              </div>
            </div>
          </a-space>
        </template>
        <template v-else-if="column.dataIndex === 'created_date'">
          <div>
            <a-typography class="text-base font-normal" style="color: #4b465c">
              {{ record.created_date }}
            </a-typography>
            <a-typography-text
              class="font-normal text-sm"
              style="color: #2f2b3d80"
              >{{ record.time }}</a-typography-text
            >
          </div>
        </template>

        <template v-else-if="column.dataIndex === 'SEX'">
          <a-typography-text>
            {{ record.status }}
          </a-typography-text>
        </template>
        <template v-else-if="column.dataIndex === 'order'">
          <a-typography-text :bordered="false">
            {{ record.Order }}
          </a-typography-text>
        </template>
        <template v-if="column.dataIndex === 'actions'">
          <NuxtLink
            :href="routes.path"
            v-for="(routes, index) in route"
            :key="index"
          >
            <Icon icon="tabler:eye" width="1.2rem" height="1.2rem" />
          </NuxtLink>
        </template>
      </template>
    </a-table>
  </a-card>
</template>
<style scoped>
/* Optional: Define responsive table styling */
@media (max-width: 768px) {
  /* .ant-table {
    overflow-x: auto;
  } */
}
</style>
