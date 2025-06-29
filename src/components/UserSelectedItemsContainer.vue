<template>
  <div class="bg-blue-500 p-2 h-[162px]">
    <div class="h-[132px]">
      <SomeItemList
        :items="items"
        @click="emit('cancel-select', $event)"
      />
    </div>
    <div class="text-center text-gray-100">
      Selected items: {{ items.length }} / {{ MAX_SELECTED_USER_ITEMS }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { MAX_SELECTED_USER_ITEMS } from '../consts';
import SomeItemList from './SomeItemList.vue';
import type { TSomeItem } from '../types';

defineProps<{
  items: TSomeItem[];
}>();

const emit = defineEmits<{
  (e: 'cancel-select', id: number): void;
}>();
</script>
