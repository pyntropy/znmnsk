# AGENTS.md

Vue 3 (JS, `<script setup>`) + Vite 8 + Tailwind CSS v4 SPA. Remote: git@github.com:pyntropy/znmnsk.git.

**Все файлы проекта лежат в `src/`** (`package.json` с зависимостями, `vite.config.js`, `index.html`, компоненты). В корне — `AGENTS.md`, `.gitignore`, `README.md`, `guides/` и тонкий `package.json`-обёртка (без зависимостей, делегирует в `src/`).

## Commands

Все команды — **из корня** (облако тоже запускает их из корня):

```sh
npm install        # ставит зависимости в src/node_modules (через postinstall в package.json корня)
npm run dev        # dev server
npm run build      # production build; ЕДИНСТВЕННЫЙ шаг верификации (lint/test/typecheck нет)
npm run preview    # serve the build
```

Корневой `package.json` — тонкая обёртка без зависимостей: скрипты делегируют в `src/` (`npm --prefix src`), `prebuild`/`postinstall` гарантируют установку зависимостей. Настоящие зависимости прописаны в `src/package.json`.

После `npm run build` артефакты появляются в `src/dist` (уже в `.gitignore`).

## Tailwind v4 setup (non-obvious)

- Включается плагином `@tailwindcss/vite` в `src/vite.config.js`; `tailwind.config.js` нет — это нормально, не добавлять.
- Единственный глобальный `@import "tailwindcss";` — в `src/assets/main.css`, импортируется из `src/main.js`.
- Никогда не импортить CSS внутри `<script>` в `.vue`; утилиты — прямо в `<template>`.

## Conventions

- Alias `@` → текущий каталог `src/` (конфиг в `src/vite.config.js` и `src/jsconfig.json`).
- Расположение компонентов (общесистемные в `src/components/`, модульные в `src/modules/<feature>/components/`) — описано в `guides/04-project-structure.md`.
- `guides/01..03-*.md` — пустые заглушки, игнорировать.
