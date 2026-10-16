# Agent workflow — Nuxt 4 Template

Этот файл читается агентом наравне с `AGENTS.md`, но в отличие от него **правится вручную**:
`AGENTS.md` генерируется из `.cursor/rules` командой `node .cursor/sync-rules.mjs`.

Полный инструментарий в репо: `.cursor/`, `AGENTS.md`, `.dsh/skills/`, `.planning/` (PROJECT, templates).
После копирования в продукт обновите `90` и `.planning/PROJECT.md`, затем `node .cursor/sync-rules.mjs` (перегенерирует `AGENTS.md` и скиллы); проверка рассинхрона — `node .cursor/check-rules.mjs`.

Синхронизация workflow: `_Cursor-rules-template` (`00`–`09`, commands); `90-project-context` — только дополнять.

## Карта правил

| Правило         | Режим                       | Назначение                             |
| --------------- | --------------------------- | -------------------------------------- |
| `00`            | **always**                  | GSD, краткий Verify                    |
| `07`            | **always**                  | Экономия токенов (чат + MCP)           |
| `08`            | **always**                  | Маршрутизация Cursor ↔ DS Harness      |
| `09`            | **requestable**             | Figma: MCP в Cursor, REST в DS Harness |
| `90`            | **always**                  | Контекст шаблона / продукта            |
| `nuxt-template` | **globs** app/server/shared | TS, Vue, SCSS, mobile-first            |
| `01`–`06`       | **requestable**             | Discuss … Principles                   |

В DS Harness `01`–`06`, `09` и globs-правила попадают скиллами в `.dsh/skills` и подгружаются по
требованию; `AGENTS.md` (always-набор) собирается тем же скриптом.

## Команды

| Команда        | Назначение              |
| -------------- | ----------------------- |
| `/brief`       | `brief.md` из шаблона   |
| `/wave-done`   | Итог волны в `state.md` |
| `/verify`      | Проверки по классу      |
| `/code-review` | Local или GitLab MR     |

MCP: User `~/.cursor/mcp.json` (nuxt, context7, figma, mdn). Проектный `.cursor/mcp.json` — пустой `mcpServers`. GitLab → GitKraken.

## Промпт агенту

```text
Класс M. Задача: … Done when: …
```

Новая сессия L+: `@.planning/PROJECT.md` `@.planning/brief.md`
