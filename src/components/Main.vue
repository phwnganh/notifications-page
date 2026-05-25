<script setup>
import MarkWebberAvatar from '../assets/avatar-mark-webber.webp'
import AngelaGray from '../assets/avatar-angela-gray.webp'
import JacobThompson from '../assets/avatar-jacob-thompson.webp'
import RizkyHasanuddin from '../assets/avatar-rizky-hasanuddin.webp'
import KimberlySmith from '../assets/avatar-kimberly-smith.webp'
import ImageChess from '../assets/image-chess.webp'
import NathanPeterson from '../assets/avatar-nathan-peterson.webp'
import AnnaKim from '../assets/avatar-anna-kim.webp'
import {computed, ref} from "vue";
import NotificationHeader from "./NotificationHeader.vue";
import NotificationItem from "./NotificationItem.vue";

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
          <NotificationHeader :onMarkAllAsRead="handleMarkAllAsRead" :unreadCount="unreadCount"/>
      <main class="flex flex-col gap-6">
          <section class="flex flex-col gap-2">
              <NotificationItem v-for="notification in notifications" :key="notification.id" :notification="notification" />
          </section>
      </main>
        </div>
    </div>
</template>

<style scoped>

</style>