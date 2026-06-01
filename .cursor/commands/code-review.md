---
description: Code review — локальные изменения или GitLab MR (номер/URL)
argument-hint: [mr-number | mr-url | пусто = local]
---

# Code Review

**Input:** $ARGUMENTS

Полный протокол — `04-verify-and-done.mdc` (security Nuxt, severity, validation).

## Режим

| Input | Режим |
|-------|-------|
| Пусто | **Local** — `git diff --name-only HEAD` |
| Номер MR или URL `…/merge_requests/N` | **GitLab MR** — MCP `review-merge-request` или `glab mr diff` |

Платформа **GitLab**, не GitHub / `gh pr`.

## Минимум

1. Прочитать затронутые файлы целиком
2. Чеклист CRITICAL → LOW (Nuxt/Nitro, `nuxt-template.mdc`)
3. `pnpm lint:all`; для L+ — `pnpm build`; pipeline для MR

## Отчёт

Решение: **OK** | **FIX REQUIRED** | **BLOCK** + pipeline status.
