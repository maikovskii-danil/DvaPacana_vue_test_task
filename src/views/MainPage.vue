<template>
  <div class="flex gap-2 shadow-xl/20 w-[450px]">
    <UserList :items="USER_ITEMS" />
    <CommonList :items="COMMON_ITEMS" />
  </div>
</template>

<script setup lang="ts">
import { COMMON_ITEMS, USER_ITEMS } from '../consts';
import CommonList from '../components/CommonSelector.vue';
import UserList from '../components/UserSelector.vue';
</script>
