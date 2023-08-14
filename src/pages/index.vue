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
  <div flex items-center justify-evenly >
    <div>
      <TheInput
        v-model="name"
        placeholder="输入路径"
        autocomplete="false"
        @keydown.enter="go"
      />

      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
  </div>
</template>
