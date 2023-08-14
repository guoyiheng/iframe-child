<script setup lang="ts" generic="T extends any, O extends any">
defineOptions({
  name: 'IndexPage',
})

const name = ref('')

const router = useRouter()
function go() {
  if (name.value)
    router.push(`/hi/${encodeURIComponent(name.value)}`)
}
</script>

<template>
  <div class="border-1px border-red-500" p-10>
    <div m-3>Child Iframe</div>
    <TheInput
      v-model="name"
      placeholder="What's your name?"
      autocomplete="false"
      @keydown.enter="go"
    />

    <div>
      <button class="m-3 text-sm btn" :disabled="!name" @click="go">
        Go
      </button>
    </div>
  </div>
</template>
