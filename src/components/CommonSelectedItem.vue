<template>
  <div
    class="h-[162px] flex items-center justify-center text-gray-100 bg-blue-500 relative"
  >
    <div
      v-if="item"
      class="bg-blue-900 border-4 border-gray-100 absolute top-1 left-1 right-1 bottom-1 flex items-center justify-center cursor-pointer hover:bg-blue-600"
      @click="emit('cancel-select')"
    >
      {{ item.name }}
    </div>
    <div v-else>Empty</div>
  </div>
</template>

<script setup lang="ts">
import type { TSomeItem } from '../types';

defineProps<{
  item: TSomeItem | null;
}>();

const emit = defineEmits<{
  (e: 'cancel-select'): void;
}>();
</script>
