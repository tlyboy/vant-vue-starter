# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 常用命令

```bash
pnpm dev          # 启动开发服务器
pnpm build        # 类型检查 + 生产构建
pnpm build-only   # 仅生产构建（不检查类型）
pnpm type-check   # 运行 vue-tsc 类型检查
pnpm preview      # 预览生产构建
```

## 技术栈

- **框架**: Vue 3 + TypeScript + Vite (rolldown-vite)
- **UI 组件库**: Vant 4
- **样式**: Tailwind CSS 4 + @egoist/tailwindcss-icons (Carbon 图标)
- **状态管理**: Pinia + pinia-plugin-persistedstate (自动持久化)
- **路由**: Vue Router + unplugin-vue-router (基于文件的路由)
- **Node 版本**: >= 22
- **包管理器**: pnpm

## 架构

### 自动导入

项目配置了广泛的自动导入，无需手动 import：

- **Vue API**: `ref`, `computed`, `watch`, `nextTick` 等
- **Vue Router**: `useRouter`, `useRoute`, `definePage` 等
- **VueUse**: `useColorMode` 等所有 composables
- **Pinia**: `defineStore`, `storeToRefs` 等
- **Vant 组件**: 所有 Vant 组件自动注册
- **自定义 composables**: `src/composables/` 目录下的函数自动导入
- **Store**: `src/stores/` 目录下的 store 自动导入

### 基于文件的路由

- 页面文件放在 `src/pages/` 目录
- 布局文件放在 `src/layouts/` 目录
- 路由自动从文件结构生成
- 使用 `definePage` 宏定义页面元信息

### 深色模式

- 使用 VueUse 的 `useColorMode()` 管理
- Vant 通过 `van-config-provider` 的 `theme` prop 同步深色模式
- CSS 使用 `@custom-variant dark (&:where(.dark, .dark *))` 定义深色变体
- 支持 View Transitions API 的圆形扩展动画效果

### 样式约定

- 全局样式在 `src/styles.css`
- 使用 Tailwind 的 `@layer components` 定义可复用样式类（如 `.btn`, `.icon-btn`）
- 图标使用 Tailwind CSS Icons 语法：`class="i-carbon-xxx"`
- Vant 主题色通过 CSS 变量 `--van-blue` 自定义

### 路径别名

- `@` 指向 `src/` 目录
