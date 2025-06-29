<template>
  <div class="flex flex-wrap gap-5">
    <SomeItem
      v-for="item in items"
      :key="item.id"
      :item="item"
      @click="emit('click', item.id)"
    />
    <div
      v-if="items.length === 0"
      class="text-gray-100"
    >
      No items
    </div>
  </div>
</template>

<script setup lang="ts">
import SomeItem from './SomeItem.vue';
import type { TSomeItem } from '../types';

defineProps<{
  items: TSomeItem[];
}>();

const emit = defineEmits<{
  (e: 'click', id: number): void;
}>();
</script>
