# AGENTS.md

This file provides guidance to AI agents when working with code in this repository.

## Common Commands

```bash
pnpm dev          # Start development server
pnpm build        # Type check + production build
pnpm build-only   # Production build only (no type checking)
pnpm type-check   # Run vue-tsc type checking
pnpm preview      # Preview production build
```

## Tech Stack

- **Framework**: Vue 3 + TypeScript + Vite (rolldown-vite)
- **UI Component Library**: Vant 4
- **Styling**: Tailwind CSS 4 + @egoist/tailwindcss-icons (Carbon icons)
- **State Management**: Pinia + pinia-plugin-persistedstate (auto persistence)
- **Routing**: Vue Router + unplugin-vue-router (file-based routing)
- **Node Version**: >= 22
- **Package Manager**: pnpm

## Architecture

### Auto Imports

The project is configured with extensive auto-imports, no manual import needed:

- **Vue API**: `ref`, `computed`, `watch`, `nextTick`, etc.
- **Vue Router**: `useRouter`, `useRoute`, `definePage`, etc.
- **VueUse**: `useColorMode` and all other composables
- **Pinia**: `defineStore`, `storeToRefs`, etc.
- **Vant Components**: All Vant components are auto-registered
- **Custom composables**: Functions in the `src/composables/` directory are auto-imported
- **Store**: Stores in the `src/stores/` directory are auto-imported

### File-Based Routing

- Page files are placed in the `src/pages/` directory
- Layout files are placed in the `src/layouts/` directory
- Routes are automatically generated from the file structure
- Use the `definePage` macro to define page meta information

### Dark Mode

- Managed using VueUse's `useColorMode()`
- Vant syncs dark mode via the `theme` prop of `van-config-provider`
- CSS uses `@custom-variant dark (&:where(.dark, .dark *))` to define dark variants
- Supports circular expand animation effect via the View Transitions API

### Styling Conventions

- Global styles are in `src/styles.css`
- Use Tailwind's `@layer components` to define reusable style classes (e.g., `.btn`, `.icon-btn`)
- Icons use Tailwind CSS Icons syntax: `class="i-carbon-xxx"`
- Vant theme color is customized via the CSS variable `--van-blue`

### Path Aliases

- `@` points to the `src/` directory
