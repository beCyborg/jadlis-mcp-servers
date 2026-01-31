# Jadlis MCP Servers

**Repo**: https://github.com/beCyborg/jadlis-mcp-servers
**Язык**: русский (issues, коммиты, документация)

---

## Что это

Монорепо MCP серверов для системы Jadlis. Каждый сервер в `packages/` предоставляет tools для Claude Code.

---

## Структура

```
jadlis-mcp-servers/
├── packages/
│   ├── obsidian/      # Obsidian Vault integration
│   ├── ticktick/      # TickTick tasks & habits
│   └── shared/        # Общие утилиты
├── package.json       # Bun workspaces
├── tsconfig.json      # TypeScript config
└── biome.json         # Linter/formatter
```

---

## Runtime

**Bun** — основной runtime (14x быстрее cold start vs Node.js)

```bash
# Установка зависимостей
bun install

# Запуск сервера в dev режиме
bun run --filter @jadlis/mcp-obsidian dev

# Тесты
bun test

# Lint
bun run lint
```

---

## Создание нового сервера

```bash
mkdir packages/my-server
cd packages/my-server
bun init
```

### Минимальный package.json

```json
{
  "name": "@jadlis/mcp-my-server",
  "version": "0.1.0",
  "type": "module",
  "main": "src/index.ts",
  "scripts": {
    "dev": "bun run src/index.ts",
    "build": "bun build src/index.ts --outdir dist --target bun",
    "test": "bun test"
  },
  "dependencies": {
    "@modelcontextprotocol/sdk": "^1.17.5"
  }
}
```

### Минимальный сервер

```typescript
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';

const server = new Server(
  { name: 'my-mcp-server', version: '0.1.0' },
  { capabilities: { tools: {} } }
);

// Регистрация tools
server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [/* ... */]
}));

server.setRequestHandler(CallToolRequestSchema, async (request) => {
  // Handle tool calls
});

const transport = new StdioServerTransport();
await server.connect(transport);
```

---

## Подход: Готовые + Wrapper

Вместо написания с нуля используем готовые решения:

| Сервер | Готовое решение | Подход |
|--------|-----------------|--------|
| Obsidian | `cyanheads/obsidian-mcp-server` | Форк или wrapper |
| TickTick | `ticktick-sdk` или `alexarevalo9` | Форк или wrapper |

---

## Тестирование

```bash
# Unit тесты
bun test

# Интерактивная отладка
npx @anthropic-ai/mcp-inspector
```

---

## Коммиты

Следуем правилам jadlis-creator:
- Каждый коммит привязан к issue
- Формат: `feat:`, `fix:`, `docs:` + описание на русском
- Ссылка: `Closes #N` или `Part of jadlis-creator#N`
