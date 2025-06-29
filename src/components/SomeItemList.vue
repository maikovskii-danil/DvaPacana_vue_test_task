<template>
  <div class="flex flex-wrap gap-5">
    <SomeItem
      v-for="itemRenderData in itemRenderDataArray"
      :key="itemRenderData.item.id"
      :item-render-data="itemRenderData"
      @click="emit('click', itemRenderData.item.id)"
    />
    <div
      v-if="itemRenderDataArray.length === 0"
      class="text-gray-100"
    >
      No items
    </div>
  </div>
</template>

<script setup lang="ts">
import SomeItem from './SomeItem.vue';
import type { TSomeItemRenderData } from '../types';

defineProps<{
  itemRenderDataArray: TSomeItemRenderData[];
}>();

const emit = defineEmits<{
  (e: 'click', id: number): void;
}>();
</script>
