# Agent workflow — Nuxt 4 Template

Полный инструментарий в репо: `.cursor/`, `AGENTS.md`, `.planning/` (PROJECT, templates, brief/plan/state).
После копирования в продукт обновите `90` и `.planning/PROJECT.md`; сессионные файлы при необходимости добавьте в gitignore продукта.

Синхронизация workflow: `_Cursor-rules-template` (`00`–`07`, commands); `90-project-context` — только дополнять.

## Карта правил

| Правило | Режим | Назначение |
| --- | --- | --- |
| `00` | **always** | GSD, краткий Verify |
| `07` | **always** | Экономия токенов (чат + MCP) |
| `90` | **always** | Контекст шаблона / продукта |
| `nuxt-template` | **globs** app/server/shared | TS, Vue, SCSS, mobile-first |
| `01`–`06` | **requestable** | Discuss … Principles |

## Команды

| Команда | Назначение |
| --- | --- |
| `/brief` | `brief.md` из шаблона |
| `/wave-done` | Итог волны в `state.md` |
| `/verify` | Проверки по классу |
| `/code-review` | Local или GitLab MR |

MCP: `.cursor/mcp.json` (nuxt, context7, опционально figma).

## Промпт агенту

```text
Класс M. Задача: … Done when: …
```

Новая сессия L+: `@.planning/PROJECT.md` `@.planning/brief.md`
