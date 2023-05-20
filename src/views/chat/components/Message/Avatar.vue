<script lang="ts" setup>
import { computed } from 'vue'
import { NAvatar } from 'naive-ui'
import { useUserStore } from '@/store'
import { isString } from '@/utils/is'
import defaultAvatar from '@/assets/user_avatar.jpg'
import defaultAvatarAI from '@/assets/ai_robot.jpg'

interface Props {
  image?: boolean
}
defineProps<Props>()

const userStore = useUserStore()

const avatar = computed(() => userStore.userInfo.avatar)
</script>

<template>
  <template v-if="image">
    <NAvatar v-if="isString(avatar) && avatar.length > 0" :src="avatar" :fallback-src="defaultAvatar" />
    <NAvatar v-else round="false" :color="white" :src="defaultAvatar" />
  </template>
  <span v-else class="text-[28px] dark:text-white">
    <NAvatar round=false :color="white" :src="defaultAvatarAI" />
  </span>
</template>
