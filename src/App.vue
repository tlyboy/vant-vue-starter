

<template>
  <van-config-provider :theme="isDark ? 'dark' : 'light'" h-full>
    <RouterView />
  </van-config-provider>
</template>
