<template>
  <div
    class="border-3 border-gray-100 text-gray-100 bg-blue-900 text-center w-30 h-30"
    @click="emit('click', item.id)"
  >
    {{ item.name }}
  </div>
</template>

<script setup lang="ts">
import type { TSomeItem } from '../types';

defineProps<{
  item: TSomeItem;
}>();

const emit = defineEmits<{
  (e: 'click', id: number): void;
}>();
</script>
