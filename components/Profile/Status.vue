<script lang="ts" setup>
import { ref } from "vue";
import { Icon } from "@iconify/vue";

const activeKey = ref("1");

const setActiveKey = (key: string) => {
  activeKey.value = key;
};
</script>

<template>
  <a-tabs v-model:activeKey="activeKey" class="w-full" :bordered="false">
    <a-tab-pane key="1" class="w-full">
      <template #tab>
        <a-button
          :type="activeKey === '1' ? 'primary' : 'default'"
          @click="setActiveKey('1')"
          class="flex"
        >
          <Icon icon="lucide:user-check" width="1.2rem" height="1.2rem" />
          <a-typography
            :class="{
              'text-white': activeKey === '1',
              'text-default': activeKey !== '1',
            }"
          >
            Profile
          </a-typography>
        </a-button>
      </template>
      <ProfileUserAllUser />
    </a-tab-pane>
    <a-tab-pane key="2">
      <template #tab>
        <a-button
          :type="activeKey === '2' ? 'primary' : 'default'"
          @click="setActiveKey('2')"
          class="flex"
        >
          <Icon icon="tabler:zoom-money" width="1.2rem" height="1.2rem" />
          <a-typography
            :class="{
              ' text-white ': activeKey === '2',
              ' text-black ': activeKey !== '2',
            }"
          >
            My Order
          </a-typography>
        </a-button>
      </template>
      <ProfileUserOder />
    </a-tab-pane>
  </a-tabs>
</template>
