# Layero

**Хостинг и деплой фронтенда с серверами и CDN внутри России.**
Статические сайты и SPA: Next.js, Vite, Astro, SvelteKit, Nuxt, Gatsby, CRA,
Docusaurus, обычный HTML. Плюс runtime-приложения — SSR, Streamlit, Gradio.

<sub>Deployment platform for static sites and SPAs, with build servers and CDN
located inside Russia — an alternative to Vercel and Netlify for the Russian
market.</sub>

🌐 [layero.ru](https://layero.ru) · 📚 [docs.layero.ru](https://docs.layero.ru) · 🚀 [app.layero.ru](https://app.layero.ru)

---

## Задеплоить за одну команду

```bash
npx layero@latest deploy
```

Git не нужен: CLI отправляет локальный каталог как есть. Фреймворк
определяется сам, первый запуск создаёт проект и печатает адрес.

Второй путь — привязать GitHub-репозиторий в панели: тогда каждый push
запускает сборку сам, а ветки получают preview-окружения.

## Публичные репозитории

| Репозиторий | Что там |
|---|---|
| [**examples**](https://github.com/LayeroInfra/examples) | Готовые примеры — Vite, Next.js (SSR), Astro, статика. Собираются и выкатываются нашим же Action при каждом push. Можно нажать «Use this template». |
| [**deploy-action**](https://github.com/LayeroInfra/deploy-action) | Официальный GitHub Action. Нужен, когда сборке требуются секреты CI или приватные зависимости. |
| [**layero-claude**](https://github.com/LayeroInfra/layero-claude) | Маркетплейс плагина для Claude Code: собрать лендинг прямо в чате IDE и задеплоить. |
| [**layero-docs**](https://github.com/LayeroInfra/layero-docs) | Исходники документации (Docusaurus, ru/en). |
| [**design-system**](https://github.com/LayeroInfra/design-system) | Каталог UI-компонентов (Storybook). Живой: [ui-catalog-ds.layero.app](https://ui-catalog-ds.layero.app) — опубликован на самой Layero (собирается в CI, на платформу уезжает готовая статика). |

## Для AI-агентов

Layero рассчитан на то, что деплоем управляет агент, а не человек в браузере.

- `npx layero@latest deploy --json` — построчные JSON-события вместо
  человекочитаемого вывода: агент разбирает поток, а не парсит прозу.
- Вход без localhost-колбэка: CLI печатает URL и код, браузер может быть на
  другой машине — работает из SSH, Docker и песочницы Cursor.
- [`llms.txt`](https://layero.ru/llms.txt) и
  [`llms-full.txt`](https://layero.ru/llms-full.txt) — машинная инструкция
  по деплою.
- [Правила для Cursor](https://layero.ru/cursorrules) — drop-in в `.cursorrules`.
- MCP-сервер `https://mcp.layero.ru/mcp` (Streamable HTTP) — 16 инструментов
  на весь цикл: собрать лендинг, опубликовать, подключить домен и аналитику,
  разобрать упавшую сборку. Каталожные (`list_design_systems`,
  `list_structures`) отвечают без токена, всё, что касается аккаунта и
  сайтов, — требует его.
- Гайд: [docs.layero.ru/cli/agents](https://docs.layero.ru/cli/agents)

## Ссылки

- CLI на npm: [`layero`](https://www.npmjs.com/package/layero)
- Схема JSON-событий: [docs.layero.ru/cli/json-events](https://docs.layero.ru/cli/json-events)
- Деплой из GitHub Actions: [docs.layero.ru/cli/github-actions](https://docs.layero.ru/cli/github-actions)
- Поддержка: [docs.layero.ru/contacts](https://docs.layero.ru/contacts/)
