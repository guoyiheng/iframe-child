<script setup lang="ts" generic="T extends any, O extends any">
import { WindowChannel } from '@haiyaotec/window-channel'

/**
 * client
 */
const messageArr = ref<string[]>([])
const client = WindowChannel.newChannelClient(window, window.parent, '*')
function sendMessage(msg: string) {
  client
    .request('/hello', `来自客户端消息${new Date().toLocaleTimeString()}: ${msg}`, 1000)
    .then((value: any) => {
      messageArr.value.push(value)
    })
    .catch((err) => {
      console.error(err)
    })
}
const route = useRoute()
watch(
  () => route.path,
  (newPath, oldPath) => {
    sendMessage(route.path)
  },
  { immediate: true },
)
</script>

<template>
  <main class="border-4px border-red-300" font-sans p="x-4 y-10" text="center gray-700 dark:gray-200">
    <div mb-10px c-red-300>
      Child Iframe
    </div>
    <RouterView />
    <ol w-full flex justify-center items-center flex-col gap-10px>
      <li v-for="item in messageArr" :key="item" class="border-1px w-400px p-4px">
        {{ item }}
      </li>
    </ol>
  </main>
</template>
