<template>
  <div class="flex flex-col gap-2 w-[50%]">
    <UserSelectedItemsContainer
      :item-render-data-array="selectedItemsRenderDataArray"
      @cancel-select="handleItemSelect"
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
import { MAX_SELECTED_USER_ITEMS } from '../consts';
import SomeItemList from './SomeItemList.vue';
import UserSelectedItemsContainer from './UserSelectedItemsContainer.vue';

const { items } = defineProps<{
  items: TSomeItem[];
}>();

const selectedItems = ref<TSomeItem[]>([]);
const selectedItemsIds = computed(() =>
  selectedItems.value.map((item) => item.id),
);

const itemRenderDataArray = computed<TSomeItemRenderData[]>(() =>
  items.map((item) => ({
    item,
    disabled: selectedItemsIds.value.includes(item.id),
  })),
);

const selectedItemsRenderDataArray = computed<TSomeItemRenderData[]>(() =>
  selectedItems.value.map((item) => ({
    item,
    disabled: false,
  })),
);

const handleItemSelect = (id: number) => {
  if (selectedItemsIds.value.includes(id)) {
    selectedItems.value = selectedItems.value.filter((item) => item.id !== id);
    return;
  }

  if (
    selectedItems.value.length < MAX_SELECTED_USER_ITEMS
    && !selectedItemsIds.value.includes(id)
  ) {
    const foundItem = items.find((item) => item.id === id);
    if (foundItem) {
      selectedItems.value.push(foundItem);
    }
  }
};
</script>
