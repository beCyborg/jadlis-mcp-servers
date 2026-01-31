# Jadlis MCP Servers

Монорепо MCP серверов для системы [Jadlis](https://github.com/beCyborg/jadlis-creator).

## Серверы

| Сервер | Статус | Описание |
|--------|--------|----------|
| `@jadlis/mcp-obsidian` | 🔜 Planned | Интеграция с Obsidian Vault |
| `@jadlis/mcp-ticktick` | 🔜 Planned | TickTick tasks & habits |
| `@jadlis/mcp-shared` | 🔜 Planned | Общие утилиты |

## Технологии

- **Runtime**: [Bun](https://bun.sh) (14x быстрее cold start vs Node.js)
- **Language**: TypeScript
- **MCP SDK**: `@modelcontextprotocol/sdk`
- **Linter**: [Biome](https://biomejs.dev)

## Быстрый старт

```bash
# Установка Bun
curl -fsSL https://bun.sh/install | bash

# Клонирование
git clone https://github.com/beCyborg/jadlis-mcp-servers.git
cd jadlis-mcp-servers

# Установка зависимостей
bun install

# Запуск тестов
bun test
```

## Документация

См. [CLAUDE.md](./CLAUDE.md) для инструкций по разработке.

## Связанные репозитории

- [jadlis-creator](https://github.com/beCyborg/jadlis-creator) — разработка и планирование
- [jadlis-vault](https://github.com/beCyborg/jadlis-vault) — Obsidian Vault
- [jadlis-bot](https://github.com/beCyborg/jadlis-bot) — Telegram bot

## Лицензия

MIT
