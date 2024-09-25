<script setup lang="ts">
import { ref, reactive } from "vue";
import { Icon } from "@iconify/vue";

import { useRouter } from "vue-router";

const router = useRouter();

const navigateHome = () => {
  router.push("/");
};
const open = ref<boolean>(false);
const showDrawer = () => {
  open.value = true;
};

const onClose = () => {
  open.value = false;
};

const state = reactive({
  routeSubMenuKeys: ["sub1"],
  openKeys: [],
  selectedKeys: [],
});

const items = ref([
  {
    path: "/customers",
  },
]);
</script>

<template>
  <!-- <SidebarLogoBongkert /> -->

  <a-layout>
    <a-layout-sider
      theme="light"
      class="hide-on-sm"
      :width="260"
      :style="{
        overflow: 'auto',
        height: 'full',
        left: 0,
        top: 0,
        bottom: 0,
        border: 'none',
      }"
    >
      <a-flex class="border-b">
        <img src="/assets/images/logo/logo.png" alt="" class="m-2" />
      </a-flex>
      <a-menu
        mode="inline"
        v-model:selectedKeys="state.selectedKeys"
        :open-keys="state.openKeys"
      >
        <a-menu-item-group>
          <template #title>
            <span class="pl-4"> General </span>
          </template>
          <a-menu-item key="dashboard" @click="navigateHome">
            <a-flex class="center gap-14">
              <div class="flex gap-2">
                <Icon icon="tabler:smart-home" class="h-5 w-5 m-auto" />
                <span>Dashboard</span>
              </div>
              <a-badge
                :count="5"
                :number-style="{
                  backgroundColor: '#005C94',
                  color: '#FFFFFF',
                }"
                class="m-auto"
              />
            </a-flex>
          </a-menu-item>
          <a-menu-item key="My_account">
            <a-flex class="center">
              <div class="flex gap-2">
                <Icon icon="ph:user-circle" class="h-5 w-5 m-auto" />
                <span> My Account</span>
              </div>
            </a-flex>
          </a-menu-item>
        </a-menu-item-group>

        <a-menu-item-group>
          <template #title>
            <span class="pl-4">Product </span>
          </template>
          <a-menu-item key="Product">
            <a-flex class="center">
              <div class="flex gap-2">
                <Icon icon="mingcute:package-2-line" class="w-5 h-5 m-auto" />
                <span> Product Management</span>
              </div>
              <Icon
                icon="material-symbols:chevron-right"
                class="m-auto h-5 w-5"
              />
            </a-flex>
          </a-menu-item>

          <a-menu-item key="add_Product">
            <span class="flex justify-center pr-6"> Add New Product</span>
          </a-menu-item>
        </a-menu-item-group>

        <a-menu-item-group>
          <template #title>
            <span class="pl-4">Store Financial Management </span>
          </template>
          <a-menu-item key="store_Financial">
            <a-flex class="center gap-12">
              <div class="flex gap-2">
                <Icon icon="tabler:report-analytics" class="h-5 w-5 m-auto" />

                <span>Store Financial</span>
              </div>
              <Icon
                icon="material-symbols:chevron-right"
                class="m-auto h-5 w-5"
              />
            </a-flex>
          </a-menu-item>
          <a-menu-item key="Payout">
            <span class="flex justify-center pr-10">Payout History</span>
          </a-menu-item>
        </a-menu-item-group>

        <a-menu-item-group>
          <template #title>
            <span class="pl-4">Store Configuration </span>
          </template>
          <a-menu-item key="Store_Config">
            <a-flex class="center gap-4">
              <div class="flex gap-2">
                <Icon icon="system-uicons:settings" class="w-5 h-5 m-auto" />
                <span> Store Configuration</span>
              </div>
              <Icon
                icon="material-symbols:chevron-right"
                class="m-auto h-5 w-5"
              />
            </a-flex>
          </a-menu-item>
          <a-menu-item key="Setting">
            <span class="flex justify-center pr-10"> General Setting</span>
          </a-menu-item>
        </a-menu-item-group>

        <a-menu-item-group>
          <template #title>
            <span class="pl-4"> My Sale</span>
          </template>
          <a-menu-item key="Sell_Order">
            <a-flex class="center justify-between gap-16">
              <div class="flex gap-2">
                <Icon icon="tabler:receipt-2" class="w-5 h-5 m-auto" />
                <span> Sell Order</span>
              </div>
              <Icon
                icon="material-symbols:chevron-right"
                class="m-auto h-5 w-5"
              />
            </a-flex>
          </a-menu-item>
          <a-menu-item key="Refund_Order">
            <a-flex class="center gap-10">
              <div class="flex gap-2">
                <Icon icon="tabler:receipt-refund" class="w-5 h-5 m-auto" />
                <span> Refund Order</span>
              </div>
              <Icon
                icon="material-symbols:chevron-right"
                class="m-auto h-5 w-5"
              />
            </a-flex>
          </a-menu-item>
          <NuxtLink
            :href="item.path"
            v-for="(item, index) in items"
            :key="index"
          >
            <a-menu-item key="All_Customer">
              <a-flex class="center gap-10">
                <div class="flex gap-2">
                  <Icon icon="tabler:user-search" class="w-5 h-5 m-auto" />
                  <span> All Customer </span>
                </div>
                <Icon
                  icon="material-symbols:chevron-right"
                  class="m-auto h-5 w-5"
                />
              </a-flex>
            </a-menu-item>
          </NuxtLink>
        </a-menu-item-group>

        <a-menu-item-group>
          <template #title>
            <span class="pl-4"> Role Management</span>
          </template>
          <a-menu-item key="Role">
            <a-flex class="center">
              <div class="flex gap-2">
                <Icon icon="tabler:users" class="h-5 w-5 m-auto" />
                <span>Role Management</span>
              </div>
              <Icon
                icon="material-symbols:chevron-right"
                class="m-auto h-5 w-5"
              />
            </a-flex>
          </a-menu-item>
          <a-menu-item key="Staff">
            <span class="flex justify-center pr-6"> Staff Management</span>
          </a-menu-item>
          <a-menu-item key="Role_management">
            <span class="flex justify-center pr-6">Role Management</span>
          </a-menu-item>
        </a-menu-item-group>
      </a-menu>
    </a-layout-sider>

    <a-layout style="min-height: 100vh">
      <a-layout-header
        :style="{ background: 'none', padding: '10px 24px 24px 24px' }"
      >
        <a-card :bodyStyle="{ padding: '13px' }" class="sticky-card">
          <div style="display: flex; align-items: center">
            <a-button type="text" @click="showDrawer" class="hide-on-md">
              <MenuOutlined />
            </a-button>
            <a-input
              placeholder="Search (Ctrl+/)"
              :bordered="false"
              size="large"
            >
              <template #prefix>
                <SearchOutlined />
              </template>
            </a-input>
            <div style="display: flex; flex-direction: row">
              <a-space :size="10">
                <a-badge :count="1">
                  <a-avatar
                    shape="circle"
                    style="background-color: #fff; color: #333; font-size: 24px"
                  >
                    <template #icon>
                      <BellOutlined />
                    </template>
                  </a-avatar>
                </a-badge>
                <a-badge dot>
                  <a-avatar shape="circle">
                    <template #icon>
                      <UserOutlined />
                    </template>
                  </a-avatar>
                </a-badge>
              </a-space>
            </div>
          </div>
        </a-card>
      </a-layout-header>
      <a-layout-content :style="{ margin: '24px 24px 0' }">
        <slot />
      </a-layout-content>
      <a-layout-footer style="text-align: center">
        Ant Design ©2018 Created by Ant UED
      </a-layout-footer>
    </a-layout>
    <a-drawer
      placement="left"
      :closable="false"
      :open="open"
      :width="250"
      @close="onClose"
      :bodyStyle="{ padding: 0 }"
    >
      <a-layout-sider
        theme="light"
        :width="260"
        :style="{
          overflow: 'auto',
          height: '100vh',
          left: 0,
          top: 0,
          bottom: 0,
          border: 'none',
        }"
      >
        <a-menu
          mode="inline"
          v-model:selectedKeys="state.selectedKeys"
          :open-keys="state.openKeys"
        >
          <a-menu-item-group>
            <template #title>
              <span class="pl-4"> General </span>
            </template>
            <a-menu-item key="dashboard">
              <NuxtLink to="/" @click="onClose">
                <a-flex class="center gap-14">
                  <div class="flex gap-2">
                    <Icon icon="tabler:smart-home" class="h-5 w-5 m-auto" />
                    <span>Dashboard</span>
                  </div>
                  <a-badge
                    :count="5"
                    :number-style="{
                      backgroundColor: '#005C94',
                      color: '#FFFFFF',
                    }"
                    class="m-auto"
                  />
                </a-flex>
              </NuxtLink>
            </a-menu-item>
            <a-menu-item key="My_account">
              <a-flex class="center">
                <div class="flex gap-2">
                  <Icon icon="ph:user-circle" class="h-5 w-5 m-auto" />
                  <span> My Account</span>
                </div>
              </a-flex>
            </a-menu-item>
          </a-menu-item-group>

          <a-menu-item-group>
            <template #title>
              <span class="pl-4">Product </span>
            </template>
            <a-menu-item key="Product">
              <a-flex class="center">
                <div class="flex gap-2">
                  <Icon icon="mingcute:package-2-line" class="w-5 h-5 m-auto" />
                  <span> Product Management</span>
                </div>
                <Icon
                  icon="material-symbols:chevron-right"
                  class="m-auto h-5 w-5"
                />
              </a-flex>
            </a-menu-item>

            <a-menu-item key="add_Product">
              <span class="flex justify-center pr-6"> Add New Product</span>
            </a-menu-item>
          </a-menu-item-group>

          <a-menu-item-group>
            <template #title>
              <span class="pl-4">Store Financial Management </span>
            </template>
            <a-menu-item key="store_Financial">
              <a-flex class="center gap-12">
                <div class="flex gap-2">
                  <Icon icon="tabler:report-analytics" class="h-5 w-5 m-auto" />

                  <span>Store Financial</span>
                </div>
                <Icon
                  icon="material-symbols:chevron-right"
                  class="m-auto h-5 w-5"
                />
              </a-flex>
            </a-menu-item>
            <a-menu-item key="Payout">
              <span class="flex justify-center pr-10">Payout History</span>
            </a-menu-item>
          </a-menu-item-group>

          <a-menu-item-group>
            <template #title>
              <span class="pl-4">Store Configuration </span>
            </template>
            <a-menu-item key="Store_Config">
              <a-flex class="center gap-4">
                <div class="flex gap-2">
                  <Icon icon="system-uicons:settings" class="w-5 h-5 m-auto" />
                  <span> Store Configuration</span>
                </div>
                <Icon
                  icon="material-symbols:chevron-right"
                  class="m-auto h-5 w-5"
                />
              </a-flex>
            </a-menu-item>
            <a-menu-item key="Setting">
              <span class="flex justify-center pr-10"> General Setting</span>
            </a-menu-item>
          </a-menu-item-group>

          <a-menu-item-group>
            <template #title>
              <span class="pl-4"> My Sale</span>
            </template>
            <a-menu-item key="Sell_Order">
              <a-flex class="center justify-between gap-16">
                <div class="flex gap-2">
                  <Icon icon="tabler:receipt-2" class="w-5 h-5 m-auto" />
                  <span> Sell Order</span>
                </div>
                <Icon
                  icon="material-symbols:chevron-right"
                  class="m-auto h-5 w-5"
                />
              </a-flex>
            </a-menu-item>
            <a-menu-item key="Refund_Order">
              <a-flex class="center gap-10">
                <div class="flex gap-2">
                  <Icon icon="tabler:receipt-refund" class="w-5 h-5 m-auto" />
                  <span> Refund Order</span>
                </div>
                <Icon
                  icon="material-symbols:chevron-right"
                  class="m-auto h-5 w-5"
                />
              </a-flex>
            </a-menu-item>
            <NuxtLink
              :href="item.path"
              v-for="(item, index) in items"
              :key="index"
            >
              <a-menu-item key="All_Customer" @click="onClose">
                <a-flex class="center gap-10">
                  <div class="flex gap-2">
                    <Icon icon="tabler:user-search" class="w-5 h-5 m-auto" />
                    <span> All Customer </span>
                  </div>
                  <Icon
                    icon="material-symbols:chevron-right"
                    class="m-auto h-5 w-5"
                  />
                </a-flex>
              </a-menu-item>
            </NuxtLink>
          </a-menu-item-group>

          <a-menu-item-group>
            <template #title>
              <span class="pl-4"> Role Management</span>
            </template>
            <a-menu-item key="Role">
              <a-flex class="center">
                <div class="flex gap-2">
                  <Icon icon="tabler:users" class="h-5 w-5 m-auto" />
                  <span>Role Management</span>
                </div>
                <Icon
                  icon="material-symbols:chevron-right"
                  class="m-auto h-5 w-5"
                />
              </a-flex>
            </a-menu-item>
            <a-menu-item key="Staff">
              <span class="flex justify-center pr-6"> Staff Management</span>
            </a-menu-item>
            <a-menu-item key="Role_management">
              <span class="flex justify-center pr-6">Role Management</span>
            </a-menu-item>
          </a-menu-item-group>
        </a-menu>
      </a-layout-sider>
    </a-drawer>
  </a-layout>
</template>
<style scoped>
.hide-on-sm {
  display: block;
}

.hide-on-md {
  display: block;
}

@media (max-width: 1024px) {
  .hide-on-sm {
    display: none;
  }
}

@media (min-width: 1025px) {
  .hide-on-md {
    display: none;
  }
}
.sticky-card {
  position: sticky;
  top: 0;
  z-index: 1000; /* Ensures the card stays on top when scrolling */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15); /* Optional for a sticky shadow effect */
}
</style>
