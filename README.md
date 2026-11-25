# DangoVault for AI assistants

Ask your AI assistant about the things you saved. [DangoVault](https://dangovault.com) turns posts you save from Instagram, TikTok, X, Threads and Bluesky into structured cards: the recipe with its ingredients and steps, the place with its address, the repo, the game, the product. This plugin connects your assistant to your library so it can search those cards and answer with the original link.

- **Read-only.** It can search and read your library. It cannot save, edit or delete anything.
- **Your decision.** Nothing is shared until you sign in to DangoVault and press **Allow**.
- **Revocable.** Disconnect it any time in DangoVault › Settings › Connected assistants.

You need a DangoVault account.

## What's inside

| File | What it does |
| --- | --- |
| `mcp.json` / `.mcp.json` | The remote MCP server: `https://app.dangovault.com/api/v1/mcp` (Streamable HTTP, OAuth 2.1 with PKCE, no API key) |
| `skills/dangovault-library/SKILL.md` | How to search the library well and how to answer from a card |
| `.cursor-plugin/plugin.json` | Plugin manifest |

## Tools

| Tool | What it returns |
| --- | --- |
| `buscar` | Cards that match keywords and filters (category, tag, done/pending, collection, facets such as country or city), with the original URL |
| `ver_ficha` | One card in full: recipe ingredients and steps, place data, product details, mentions, and each source's original URL |
| `colecciones` | Your collections and the ones shared with you |
| `categorias` | The library's categories |
| `trabajos` | Saves that are still being read or did not finish |

All tools are annotated `readOnlyHint: true`.

## Connect without the plugin

The server is a plain URL; any MCP client with OAuth support works.

- **Grok Bot:** Add a custom connector › Remote HTTPS › `https://app.dangovault.com/api/v1/mcp`.
- **Claude (claude.ai or desktop):** Settings › Connectors › Add custom connector › paste the URL › Connect.
- **Claude Code:** `claude mcp add --transport http dangovault https://app.dangovault.com/api/v1/mcp`, then run `/mcp` to sign in.
- **Cursor:** add to `.cursor/mcp.json`:

  ```json
  { "mcpServers": { "dangovault": { "url": "https://app.dangovault.com/api/v1/mcp" } } }
  ```

Your browser opens DangoVault's sign-in and consent screen. After **Allow**, the client gets a read-only token. It expires after 90 days without use; then you sign in again.

## Example prompts

- "What was that ramen place in Tokyo I saved?"
- "Give me the ingredients of the lasagna recipe I saved last month."
- "Which MCP repos did I save? Compare them."

## Privacy

See [PRIVACY.md](PRIVACY.md) and https://app.dangovault.com/privacidad. Support: soporte@dangovault.com.

## License

MIT
