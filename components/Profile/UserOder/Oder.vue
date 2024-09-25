<template>
  <a-card :body-style="{ padding: '0' }" class="pt-4">
    <!-- <div class="px-4 pt-4">
        <a-typography-text class="font-medium text-lg" style="color: #4b465c"
          >Search Filter</a-typography-text
        >
      </div> -->
    <!-- <a-divider class="my-4" /> -->
    <a-row :gutter="16" style="margin-left: 8px; margin-right: 8px">
      <a-col :span="8">
        <a-input-search placeholder="Search" class="w-full" />
      </a-col>
      <a-col :span="8">
        <a-select placeholder="KYC" style="width: 100%"></a-select>
      </a-col>

      <a-col :span="8">
        <a-range-picker v-model:value="date" class="w-full" />
      </a-col>
    </a-row>

    <a-divider class="mt-4 mb-0" />

    <a-table
      :columns="columns"
      :data-source="data"
      :row-selection="{
        selectedRowKeys: state.selectedRowKeys,
        onChange: onSelectChange,
      }"
      :scroll="{ x: 'max-content' }"
    >
      <template #bodyCell="{ column, record }">
        <template v-if="column.dataIndex === 'order_info'">
          <a-space>
            <div>
              <a-typography-text
                class="text-base font-medium"
                style="color: #005c94"
                >{{ record.order_info }}</a-typography-text
              >
              <a-flex :gap="10">
                <a-typography-text
                  class="font-normal text-sm"
                  style="color: #222222"
                  >Items : {{ record.items }}</a-typography-text
                >
                <a-tag :color="getorderColor(record.status)" :bordered="false">
                  {{ record.status }}
                </a-tag>
              </a-flex>
            </div>
          </a-space>
        </template>
        <template v-if="column.dataIndex === 'date'">
          <a-space>
            <a-flex vertical>
              <a-typography-text
                class="font-normal text-base"
                style="color: #2f2b3db2"
                >{{ record.date }}</a-typography-text
              >
              <a-typography-text
                class="font-normal text-sm"
                style="color: #2f2b3d80"
                >{{ record.time }}</a-typography-text
              >
            </a-flex>
          </a-space>
        </template>
        <template v-if="column.dataIndex === 'total'">
          <a-space>
            <a-typography-text
              class="font-normal text-base"
              style="color: #2f2b3db2"
              >{{ record.total }}</a-typography-text
            >
          </a-space>
        </template>
        <template v-if="column.dataIndex === 'delivery'">
          <a-space>
            <a-typography-text
              class="font-normal text-base"
              style="color: #2f2b3db2"
              >{{ record.delivery }}</a-typography-text
            >
          </a-space>
        </template>
        <!-- <template v-if="column.dataIndex === 'customer'">
            <a-space>
              <a-flex vertical>
                <a-typography-text
                  class="font-normal text-base"
                  style="color: #2f2b3db2"
                  >{{ record.customer }}</a-typography-text
                >
                <a-typography-link href=" " target="_blank">
                  {{ record.name }}
                </a-typography-link>
              </a-flex>
            </a-space>
          </template> -->
        <template v-if="column.dataIndex === 'order_status'">
          <a-space>
            <div v-if="record.order_status === 'Closed'">
              <a-typography-text class="font-semibold text-sm" type="success">
                <CheckCircleOutlined class="mr-2" />{{ record.order_status }}
              </a-typography-text>
            </div>
            <div v-if="record.order_status === 'Completed'">
              <a-typography-text class="font-semibold text-sm" type="success">
                <CheckCircleOutlined class="mr-2" />{{ record.order_status }}
              </a-typography-text>
            </div>
            <a-flex
              align="center"
              v-if="record.order_status === 'Reject '"
              gap="5"
            >
              <Icon
                icon="tabler:shopping-cart-off"
                width="18"
                height="18"
                style="color: #ff5b5b"
              />
              <a-typography-text class="font-semibold text-sm" type="danger">
                {{ record.order_status }}
              </a-typography-text>
            </a-flex>
            <a-flex
              align="center"
              v-if="record.order_status === 'On Delivery'"
              gap="5"
            >
              <Icon
                icon="tabler:truck-delivery"
                width="18"
                height="18"
                style="color: #005c94"
              />
              <a-typography-text
                class="font-semibold text-sm"
                style="color: #005c94"
              >
                {{ record.order_status }}
              </a-typography-text>
            </a-flex>
            <a-flex
              align="center"
              v-if="record.order_status === 'Pick Up'"
              gap="5"
            >
              <Icon
                icon="tabler:motorbike"
                width="18"
                height="18"
                style="color: #005c94"
              />
              <a-typography-text
                class="font-semibold text-sm"
                style="color: #005c94"
              >
                {{ record.order_status }}
              </a-typography-text>
            </a-flex>
            <a-flex
              align="center"
              v-if="record.order_status === 'Pending'"
              gap="5"
            >
              <Icon
                icon="tabler:loader"
                width="18"
                height="18"
                style="color: #005c94"
              />
              <a-typography-text
                class="font-semibold text-sm"
                style="color: #005c94"
              >
                {{ record.order_status }}
              </a-typography-text>
            </a-flex>
            <a-flex
              align="center"
              v-if="record.order_status === 'Arrived'"
              gap="5"
            >
              <Icon
                icon="tabler:map-pins"
                width="18"
                height="18"
                style="color: #005c94"
              />
              <a-typography-text
                class="font-semibold text-sm"
                style="color: #005c94"
              >
                {{ record.order_status }}
              </a-typography-text>
            </a-flex>
          </a-space>
        </template>
        <template v-if="column.dataIndex === 'actions'">
          <a-space class="-mt-2">
            <!-- <Icon icon="tabler:eye" width="24" height="24" @click="showModal" />
              <Icon icon="tabler:dots-vertical" width="24" height="24" /> -->
            <a-button class="bg-[#00CFE8] text-white"> Detail </a-button>
          </a-space>
        </template>
      </template>
    </a-table>
  </a-card>
</template>

<!-- <a-modal
    v-model:open="open"
    @ok="handleOk"
    :footer="null"
    width="52%"
  >
    <a-row class="mb-4">
      <a-typography-text
        style="color: #5c576b"
        class="text-2xl font-semibold"
        >Product Preview</a-typography-text
      >
    </a-row>
    <a-row :gutter="10">
      <a-col :span="3">
        <a-row class="my-2" v-for="(img, index) in images" :key="index">
          <img
            :src="img"
            alt=""
            @click="setMainImage(img)"
            class="thumbnail"
          />
        </a-row>
      </a-col>
      <a-col :span="11" class="my-2">
        <a-image width="100%" height="100%" :src="mainImage" />
      </a-col>
      <a-col :span="10">
        <div class="pl-2">
          <a-typography-text
            class="font-bold text-2xl"
            style="color: #333333"
            >{{ product.title }}</a-typography-text
          >
          <a-flex gap="10">
            <a-typography-text
              class="text-3xl font-medium"
              style="color: #005c94"
              >${{ product.currentPrice }}</a-typography-text
            >
            <a-typography-text
              class="text-3xl font-medium"
              delete
              type="danger"
              >${{ product.originalPrice }}</a-typography-text
            >
          </a-flex>
          <a-typography-text
            class="font-normal text-base"
            style="color: #333333"
            >{{ product.description }}</a-typography-text
          >
          <div class="border border-gray-200 my-4"></div>
          <a-flex>
            <a-flex vertical gap="10" class="mr-4">
              <a-typography-text
                class="font-normal text-base"
                style="color: #666666"
                >Color:
              </a-typography-text>
              <a-typography-text
                class="font-normal text-base"
                style="color: #666666"
                >Size:
              </a-typography-text>
              <a-typography-text
                class="font-normal text-base"
                style="color: #666666"
                >Brand:
              </a-typography-text>
              <a-typography-text
                class="font-normal text-base"
                style="color: #666666"
                >Category:
              </a-typography-text>
              <a-typography-text
                class="font-normal text-base"
                style="color: #666666"
                >Sub Category:
              </a-typography-text>
            </a-flex>
            <a-flex vertical gap="10">
              <div class="rounded-full w-5 h-5 bg-yellow-600"></div>
              <a-typography-text
                class="font-normal text-base"
                style="color: #666666"
                >{{ product.size }}</a-typography-text
              >
              <a-typography-text
                class="font-normal text-base"
                style="color: #666666"
                >{{ product.brand }}
              </a-typography-text>
              <a-typography-text
                class="font-normal text-base"
                style="color: #333333"
                >{{ product.category }}
              </a-typography-text>
              <a-typography-text
                class="font-normal text-base"
                style="color: #333333"
                >{{ product.subCategory }}
              </a-typography-text>
            </a-flex>
          </a-flex>
          <div class="border border-gray-200 my-4"></div>
          <a-flex vertical gap="10">
            <a-typography-text
              class="text-base font-semibold"
              style="color: #4b465c"
              >Package</a-typography-text
            >
            <a-typography-text
              >Weight : {{ product.weight }}
            </a-typography-text>
            <a-row>
              <a-col :span="7">
                <a-typography-text
                  class="font-normal text-base"
                  style="color: #666666"
                >
                  Length : {{ product.Length }} cm
                </a-typography-text>
              </a-col>
              <a-col :span="7">
                <a-typography-text
                  class="font-normal text-base"
                  style="color: #666666"
                >
                  Width : {{ product.Width }} cm
                </a-typography-text>
              </a-col>
              <a-col :span="7">
                <a-typography-text
                  class="font-normal text-base"
                  style="color: #666666"
                >
                  Height : {{ product.Height }} cm
                </a-typography-text>
              </a-col>
            </a-row>
          </a-flex>
        </div>
      </a-col>
    </a-row>
  </a-modal> -->
<script lang="ts" setup>
import { ref } from "vue";
import { Icon } from "@iconify/vue";
// const open = ref<boolean>(false);
// const showModal = () => {
//   open.value = true;
// };

// const handleOk = (e: MouseEvent) => {
//   console.log(e);
//   open.value = false;
// };

// const images = ref([
//   "https://i.pinimg.com/236x/9c/f7/93/9cf793634e25468e216a1233b3cf1eff.jpg",
//   "https://i.pinimg.com/474x/35/32/57/3532575f431f2fc0670f12ed9e62e43d.jpg",
//   "https://i.pinimg.com/736x/03/f7/47/03f74718e161ea25d2bef4a8f1186543.jpg",
//   "https://i.pinimg.com/236x/bc/90/a0/bc90a040c32e5082467bf55bd149103c.jpg",
// ]);

// const mainImage = ref(images.value[0]);

// const setMainImage = (img: string) => {
//   mainImage.value = img;
// };
// const product = ref({
//   title: "Dark yellow lace cut out swing dress",
//   currentPrice: "76.00",
//   originalPrice: "95.00",
//   description:
//     "Some quick example text to build on the card title and make up the bulk of the card's content.",
//   color: ["Yellow", "Black", "Blue"],
//   size: "XL",
//   brand: "Puma",
//   category: "Dresses",
//   subCategory: "Women",
//   weight: "12kg",
//   Length: "12 ",
//   Width: "12 ",
//   Height: "12 ",
// });

const columns = [
  {
    title: "ORDER INFO",
    dataIndex: "order_info",
  },
  {
    title: "DATE",
    dataIndex: "date",
  },
  // {
  //   title: "CUSTOMER",
  //   dataIndex: "customer",
  // },
  {
    title: "TOTAL",
    dataIndex: "total",
  },
  {
    title: "DELIVERY",
    dataIndex: "delivery",
  },
  {
    title: "ORDER STATUS",
    dataIndex: "order_status",
  },
  {
    title: "ACTIONS",
    dataIndex: "actions",
  },
];

type Key = string | number;
enum Status {
  COD = "COD",
  Online = "Online ",
}

enum OrderStatus {
  Closed = "Closed",
}

interface DataItem {
  key: Key;
  order_info: string;
  date: string;
  customer: string;
  total: string;
  status: Status;
  // active: boolean;
  time: string;
  name: string;
  delivery: string;
  items: number;
  order_status: OrderStatus;
}

const data: Ref<DataItem[]> = ref([
  {
    key: 1,
    order_info: "#75694",
    date: "09 May 2022",
    customer: "096449886",
    total: "$5.40.00",
    order_status: OrderStatus.Closed,
    time: "11:00 PM",
    // name: "Phorn Vannarith",
    items: 22,
    // active: true,
    status: Status.COD,
    delivery: "$5.00",
  },

  {
    key: 1,
    order_info: "#75694",
    date: "09 May 2022",
    customer: "096449886",
    total: "$5.40.00",
    order_status: OrderStatus.Closed,
    time: "11:00 PM",
    // name: "Phorn Vannarith",
    items: 22,
    // active: true,
    status: Status.COD,
    delivery: "$5.00",
  },

  {
    key: 1,
    order_info: "#75694",
    date: "09 May 2022",
    customer: "096449886",
    total: "$5.40.00",
    order_status: OrderStatus.Closed,
    time: "11:00 PM",
    // name: "Phorn Vannarith",
    items: 22,
    // active: true,
    status: Status.COD,
    delivery: "$5.00",
  },
  {
    key: 1,
    order_info: "#75694",
    date: "09 May 2022",
    customer: "096449886",
    total: "$5.40.00",
    order_status: OrderStatus.Closed,
    time: "11:00 PM",
    // name: "Phorn Vannarith",
    items: 22,
    // active: true,
    status: Status.COD,
    delivery: "$5.00",
  },
  {
    key: 1,
    order_info: "#75694",
    date: "09 May 2022",
    customer: "096449886",
    total: "$5.40.00",
    order_status: OrderStatus.Closed,
    time: "11:00 PM",
    // name: "Phorn Vannarith",
    items: 22,
    // active: true,
    status: Status.COD,
    delivery: "$5.00",
  },
  {
    key: 1,
    order_info: "#75694",
    date: "09 May 2022",
    customer: "096449886",
    total: "$5.40.00",
    order_status: OrderStatus.Closed,
    time: "11:00 PM",
    // name: "Phorn Vannarith",
    items: 22,
    // active: true,
    status: Status.COD,
    delivery: "$5.00",
  },
]);

const search = ref("");

const state = reactive<{
  selectedRowKeys: Key[];
  loading: boolean;
}>({
  selectedRowKeys: [], // Check here to configure the default column
  loading: false,
});

const onSelectChange = (selectedRowKeys: Key[]) => {
  console.log("selectedRowKeys changed: ", selectedRowKeys);
  state.selectedRowKeys = selectedRowKeys;
};

function getorderColor(status: Status) {
  switch (status) {
    case Status.COD:
      return "#FF9F43";
    default:
      return "#52C41A";
  }
}

function getProductColor(status: OrderStatus) {
  switch (status) {
    case OrderStatus.Closed:
      return "#52C41A";
    // case OrderStatus.Completed:
    //   return "#52C41A";
    // case OrderStatus.Reject:
    //   return "#FF5B5B";
    // default:
    //   return "#005C94";
  }
}
</script>

<style scoped>
:deep(.ant-table-wrapper table tr th.ant-table-selection-column) {
  padding-left: 20px;
}

:deep(.ant-table-wrapper table tr td.ant-table-selection-column) {
  padding-left: 20px;
}

.thumbnail {
  width: 100%;
  cursor: pointer;
}

.product-details {
  padding: 20px;
}

.price {
  font-size: 24px;
}

.current-price {
  color: #f5222d;
  margin-right: 10px;
}

.original-price {
  text-decoration: line-through;
  color: #8c8c8c;
}

.package {
  margin-top: 20px;
}
</style>
