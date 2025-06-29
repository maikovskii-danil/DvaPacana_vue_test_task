<template>
  <button
    class="border-3 border-gray-100 text-gray-100 bg-blue-900 text-center w-30 h-30 cursor-pointer hover:bg-blue-600 disabled:bg-gray-600 disabled:cursor-not-allowed"
    :disabled="itemRenderData.disabled"
    @click="emit('click', itemRenderData.item.id)"
  >
    {{ itemRenderData.item.name }}
  </button>
</template>

<script setup lang="ts">
import type { TSomeItemRenderData } from '../types';

defineProps<{
  itemRenderData: TSomeItemRenderData;
}>();

const emit = defineEmits<{
  (e: 'click', id: number): void;
}>();
</script>
