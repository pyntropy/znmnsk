# AGENTS.md

Vue 3 (JS, `<script setup>`) + Vite 8 + Tailwind CSS v4 SPA. Remote: git@github.com:pyntropy/znmnsk.git.

**Все файлы проекта лежат в `src/`** (`package.json`, `vite.config.js`, `index.html`, компоненты). В корне — только `AGENTS.md`, `.gitignore`, `README.md` и `guides/`.

## Commands

Все команды запускаются **из корня** флагами `--prefix src` (без `cd`):

```sh
npm --prefix src run dev      # dev server
npm --prefix src run build    # production build; ЕДИНСТВЕННЫЙ шаг верификации (lint/test/typecheck нет)
npm --prefix src run preview  # serve the build
```

После `npm --prefix src run build` артефакты появляются в `src/dist` (уже в `.gitignore`).

## Tailwind v4 setup (non-obvious)

- Включается плагином `@tailwindcss/vite` в `src/vite.config.js`; `tailwind.config.js` нет — это нормально, не добавлять.
- Единственный глобальный `@import "tailwindcss";` — в `src/assets/main.css`, импортируется из `src/main.js`.
- Никогда не импортить CSS внутри `<script>` в `.vue`; утилиты — прямо в `<template>`.

## Conventions

- Alias `@` → текущий каталог `src/` (конфиг в `src/vite.config.js` и `src/jsconfig.json`).
- Расположение компонентов (общесистемные в `src/components/`, модульные в `src/modules/<feature>/components/`) — описано в `guides/04-project-structure.md`.
- `guides/01..03-*.md` — пустые заглушки, игнорировать.
