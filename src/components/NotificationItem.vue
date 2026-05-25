<script setup>

import RedDot from "./uis/RedDot.vue";

defineProps({
  notification: Object
})
</script>

<template>
  <div class="py-4 px-6 flex sm:items-center gap-4 rounded-lg" :class="{'bg-navy-50': notification.unread}">
    <div class="flex justify-center items-center w-10 sm:w-11 h-10 sm:h-11 shrink-0">
      <img :src="notification.avatar" :alt="notification.user" />
    </div>
    <div class="flex flex-1 flex-col gap-2">
      <div class="flex flex-wrap min-w-0 sm:items-center gap-2 text-preset-4 sm:text-preset-3 leading-preset-4 sm:leading-preset-3">
        <p class="text-navy-950 font-preset-3-bold cursor-pointer hover:text-blue-950">{{notification.user}}</p>
        <span class="text-gray-600 font-preset-3-medium">{{notification.action}}</span>
        <span v-if="notification.target" class="font-preset-3-bold cursor-pointer hover:text-blue-950" :class="notification.user === 'Jacob Thompson' || notification.user === 'Anna Kim' ? 'text-blue-950': 'text-gray-600'">{{notification.target}}</span>
        <RedDot v-if="notification.unread"/>
      </div>
      <span class="text-gray-500 text-preset-4 sm:text-preset-3 leading-preset-4 sm:leading-preset-3 font-preset-3-medium">{{notification.time}}</span>

      <div v-if="notification.message" class="py-4 px-6 rounded-5 border border-navy-100 cursor-pointer hover:bg-blue-100">
        <p class="text-gray-600 text-preset-4 sm:text-preset-3 leading-preset-4 sm:leading-preset-3 font-preset-3-medium">{{notification.message}}</p>
      </div>
    </div>

    <div v-if="notification.image" class="flex justify-center items-center w-10 sm:w-11 h-10 sm:h-11 shrink-0">
      <img :src="notification.image" alt="image-chess" class="rounded-7"/>
    </div>
  </div>
</template>

<style scoped>

</style>