<script setup lang="ts">
const router = useRouter()
function goHome() {
  router.push('/')
}
</script>

<template>
  <div>
    Child Iframe
  </div>
  <button
    btn
    @click="goHome"
  >
    Refresh page
  </button>
</template>
