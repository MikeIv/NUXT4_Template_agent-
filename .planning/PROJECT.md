# Nuxt 4 Template — PROJECT

Постоянный контекст для агента (Cursor / DS Harness). **Обновите после копирования шаблона в продуктовый репозиторий.**

## Назначение

Универсальный стартовый каркас: Nuxt 4.5, Vue 3, TypeScript, Nitro, ESLint + Prettier + Stylelint, Husky, SCSS-токены (`--fs-*`), HTTP API (`useApi`, `useApiFetch`, `serverApi`).

## Стек

| Слой     | Технология                                        |
| -------- | ------------------------------------------------- |
| Frontend | Nuxt 4.5, Vue 3, SSR включён                      |
| Lint     | ESLint (@nuxt/eslint), Prettier, Stylelint, Husky |
| Стили    | SCSS, CSS Modules, mobile-first (`from-*`)        |
| API      | `runtimeConfig.public.apiBase`                    |
| PM       | pnpm 11.x                                         |

## Ключевые пути

| Путь                                  | Назначение                |
| ------------------------------------- | ------------------------- |
| `app/pages/`                          | Маршруты                  |
| `app/layouts/default.vue`             | Layout                    |
| `app/composables/useApi.ts`           | HTTP клиент               |
| `server/utils/serverApi.ts`           | API с Nitro               |
| `shared/utils/normalizeApiBaseUrl.ts` | URL API                   |
| `app/assets/styles/`                  | Глобальные стили и токены |
| `types/nuxt-public.d.ts`              | Типы `public.apiBase`     |

## Команды

```bash
pnpm install
pnpm dev
pnpm typecheck
pnpm verify
pnpm build
pnpm lint:all
```

## Новый проект из шаблона

1. Скопировать репозиторий / fork
2. Переименовать `package.json`, README, главную страницу
3. Обновить `90-project-context.mdc` и этот файл
4. `node .cursor/sync-rules.mjs` — пересобрать `AGENTS.md` и `.dsh/skills`
5. `cp .env.example .env`
6. `pnpm install` → `pnpm verify` → `pnpm build`

## Cursor rules (в git шаблона)

- Эталон workflow: внешний репозиторий-источник `_Cursor-rules-template` (`00`–`09`, `commands`)
- В шаблоне: `.cursor/` (rules, commands, пустой `mcp.json`), `AGENTS.md`, `.dsh/skills/`, `PROJECT.md` и `*-template.md`
- Генерация: `node .cursor/sync-rules.mjs` → `AGENTS.md` + `.dsh/skills`; рассинхрон ловит `node .cursor/check-rules.mjs`
- MCP: User `~/.cursor/mcp.json`; проектный `mcpServers` не заполнять
- Сессионные `brief.md` / `plan.md` / `state.md` и `.planning/figma/` — в `.gitignore`, и в шаблоне, и в продукте
- always: `00`, `07`, `08`, `90` · globs: `nuxt-template` · requestable: `01`–`06`, `09`
- Slash: `/brief` `/wave-done` `/verify` `/code-review`

## Ограничения для агента

- API только через `useApi` / `useApiFetch` / `serverApi`
- Стили: `--fs-*`, mobile-first, без desktop-first `max-width`
- Не коммитить `.env`
- Минимальный diff, без лишнего рефакторинга
