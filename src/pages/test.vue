<script setup lang="ts">
const name = 'test'
onMounted(() => {
  // eslint-disable-next-line no-console
  console.log('mounted')
})
</script>

<template>
  <div>
    hello, {{ name }}
  </div>
</template>
