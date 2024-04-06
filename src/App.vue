<template>
  <van-config-provider class="h-full" :theme="isDark ? 'dark' : 'light'" >
    <RouterView />
  </van-config-provider>
</template>
