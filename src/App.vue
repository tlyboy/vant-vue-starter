<template>
  <VanConfigProvider class="h-full" :theme="isDark ? 'dark' : 'light'">
    <RouterView />
  </VanConfigProvider>
</template>
