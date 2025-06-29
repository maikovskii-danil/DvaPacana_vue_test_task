<template>
  <div class="w-[50%] flex flex-col gap-2">
    <CommonSelectedItem
      :item="selectedItem"
      @cancel-select="selectedItem = null"
    />
    <div class="bg-blue-700 p-2">
      <SomeItemList
        :item-render-data-array="itemRenderDataArray"
        @click="handleItemSelect"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';

import type { TSomeItem, TSomeItemRenderData } from '../types';
import CommonSelectedItem from './CommonSelectedItem.vue';
import SomeItemList from './SomeItemList.vue';

const { items } = defineProps<{
  items: TSomeItem[];
}>();

const selectedItem = ref<TSomeItem | null>(null);

const itemRenderDataArray = computed<TSomeItemRenderData[]>(() =>
  items.map((item) => ({
    item,
    disabled: false,
  })),
);

const handleItemSelect = (id: number) => {
  selectedItem.value = items.find((item) => item.id === id) || null;
};
</script>
