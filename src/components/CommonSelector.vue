<template>
  <div class="w-[50%] flex flex-col gap-2">
    <CommonSelectedItem
      :item="selectedItem"
      @cancel-select="selectedItem = null"
    />
    <div class="bg-blue-700 p-2">
      <SomeItemList
        :items="items"
        @click="handleItemSelect"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

import CommonSelectedItem from './CommonSelectedItem.vue';
import SomeItemList from './SomeItemList.vue';
import type { TSomeItem } from '../types';

const { items } = defineProps<{
  items: TSomeItem[];
}>();

const selectedItem = ref<TSomeItem | null>(null);

const handleItemSelect = (id: number) => {
  selectedItem.value = items.find((item) => item.id === id) || null;
};
</script>
