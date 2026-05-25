<script setup>
  defineProps({
    unreadCount: Number,
    onMarkAllAsRead: Function,
  })
</script>

<template>
  <header class="flex justify-between sm:items-center">
    <div class="flex sm:items-center gap-2 sm:gap-4">
      <h1 class="text-preset-2 sm:text-preset-1 leading-preset-2 sm:leading-preset-1 font-preset-1 text-navy-950">Notifications</h1>
      <div class="rounded-6 px-2 py-0.5 bg-blue-950 text-white text-preset-3 leading-preset-3 font-preset-3-bold">{{unreadCount}}</div>
    </div>
    <button type="button" @click="onMarkAllAsRead" class="text-gray-600 text-preset-4 sm:text-preset-3 leading-preset-4 sm:leading-preset-3 font-preset-3-medium cursor-pointer hover:text-blue-950">Mark all as read</button>
  </header>
</template>

<style scoped>

</style>