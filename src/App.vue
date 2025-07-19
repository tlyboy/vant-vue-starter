<script setup lang="ts">
const color = useColorMode()
</script>

<template>
  <van-config-provider
    :theme="color === 'dark' ? 'dark' : 'light'"
    class="h-full"
  >
    <RouterView />
  </van-config-provider>
</template>
