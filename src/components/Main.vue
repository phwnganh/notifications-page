<script setup>
import MarkWebberAvatar from '../assets/avatar-mark-webber.webp'
import AngelaGray from '../assets/avatar-angela-gray.webp'
import JacobThompson from '../assets/avatar-jacob-thompson.webp'
import RizkyHasanuddin from '../assets/avatar-rizky-hasanuddin.webp'
import KimberlySmith from '../assets/avatar-kimberly-smith.webp'
import ImageChess from '../assets/image-chess.webp'
import NathanPeterson from '../assets/avatar-nathan-peterson.webp'
import AnnaKim from '../assets/avatar-anna-kim.webp'
import RedDot from "./uis/RedDot.vue";
import {computed, ref} from "vue";

const notifications = ref([
  {
    id: 1,
    user: 'Mark Webber',
    avatar: MarkWebberAvatar,
    action: 'reacted to your recent post',
    target: 'My first tournament today!',
    time: '1m ago',
    unread: true
  },
  {
    id: 2,
    user: 'Angela Gray',
    avatar: AngelaGray,
    action: 'followed you',
    time: '5m ago',
    unread: true
  },
  {
    id: 3,
    user: 'Jacob Thompson',
    avatar: JacobThompson,
    action: 'has joined your group',
    target: 'Chess Club',
    time: '1 day ago',
    unread: true
  },
  {
    id: 4,
    user: 'Rizky Hasanuddin',
    avatar: RizkyHasanuddin,
    action: 'sent you a private message',
    time: '5 days ago',
    message: 'Hello, thanks for setting up the Chess Club. I’ve been a member for a few weeks now and I’m already having lots of fun and improving my game.',
    unread: false
  },
  {
    id: 5,
    user: 'Kimberly Smith',
    avatar: KimberlySmith,
    action: 'commented on your picture',
    image: ImageChess,
    time: '1 week ago',
    unread: false
  },
  {
    id: 6,
    user: 'Nathan Peterson',
    avatar: NathanPeterson,
    action: 'reacted to your recent post',
    target: '5 end-game strategies to increase your win rate',
    time: '1 week ago',
    unread: false
  },
  {
    id: 7,
    user: 'Anna Kim',
    avatar: AnnaKim,
    action: 'left the group',
    target: 'Chess Club',
    time: '2 weeks ago',
    unread: false
  }
])

const handleMarkAllAsRead = () => {
  notifications.value.forEach(notification => {
    notification.unread = false;
  })
}

const unreadCount = computed(() => {
  return notifications.value.filter(notification => notification.unread).length
})
</script>

<template>
    <div class="bg-white max-w-183 w-full mx-auto rounded-15">
        <div class="py-6 px-8 flex flex-col gap-8">
        <header class="flex justify-between sm:items-center">
            <div class="flex sm:items-center gap-2 sm:gap-4">
                <h1 class="text-preset-2 sm:text-preset-1 leading-preset-2 sm:leading-preset-1 font-preset-1 text-navy-950">Notifications</h1>
                <div class="rounded-6 px-2 py-0.5 bg-blue-950 text-white text-preset-3 leading-preset-3 font-preset-3-bold">{{unreadCount}}</div>
            </div>

            <button type="button" @click="handleMarkAllAsRead" class="text-gray-600 text-preset-4 sm:text-preset-3 leading-preset-4 sm:leading-preset-3 font-preset-3-medium cursor-pointer hover:text-blue-950">Mark all as read</button>
        </header>
      <main class="flex flex-col gap-6">
          <section class="flex flex-col gap-2">
            <div v-for="notification in notifications" :key="notification.id" class="py-4 px-6 flex sm:items-center gap-4 rounded-lg" :class="{'bg-navy-50': notification.unread}">
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
                <img :src="ImageChess" alt="image-chess" class="rounded-7"/>
              </div>
            </div>
          </section>
      </main>
        </div>
    </div>
</template>

<style scoped>

</style>