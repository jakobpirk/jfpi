# JFPI: Just Fucking Prompt It

"Let Me Google That For You", for the AI era. Someone asked you something they could have asked an AI? Send them a JFPI link: they watch their question being typed into an AI, then get a cheeky answer in the tone you picked (mild, rude or brutal).

**Website:** https://www.justfuckingprompt.it · **All integrations:** https://www.justfuckingprompt.it/integrations

This repository holds JFPI's public releases (the `jfpi` command-line tool and the JFPI Bar Windows app) and the documentation for its MCP server.

## MCP server

Your AI assistant makes the JFPI link for you.

- **Remote (Streamable HTTP, no login):** `https://www.justfuckingprompt.it/mcp`
- **Local (stdio):** `npx -y jfpi-mcp` ([npm](https://www.npmjs.com/package/jfpi-mcp))

| Client | How |
|---|---|
| Claude (web, desktop, mobile) | Settings → Connectors → Add custom connector → `https://www.justfuckingprompt.it/mcp` |
| Claude Code | `claude mcp add --transport http jfpi https://www.justfuckingprompt.it/mcp` |
| Cursor (`~/.cursor/mcp.json`) | `{ "mcpServers": { "jfpi": { "url": "https://www.justfuckingprompt.it/mcp" } } }` |
| VS Code | `code --add-mcp '{"name":"jfpi","type":"http","url":"https://www.justfuckingprompt.it/mcp"}'` |
| Anything that runs a command | `{ "mcpServers": { "jfpi": { "command": "npx", "args": ["-y", "jfpi-mcp"] } } }` |

Then ask: *"Make a JFPI link for my coworker. They asked me how to exit vim."*

### Tools

| Tool | Input | Output |
|---|---|---|
| `create_jfpi_link` | `question` (string, required, 1–500 characters), `tone` (`mild`, `rude` or `brutal`; optional, default `mild`) | `url`, `tone`, and `line`: a short line in that tone to say alongside the link |
| `list_tones` | none | the three tones, each with a description and an example |

The tools are meant for links the user asks for, for someone else. The descriptions tell assistants never to use them on their own initiative or to mock the user. Every question is moderated by the site. No login and no cookies; usage is counted per assistant, never per person.

## Command line: `jfpi`

```sh
npx jfpi-cli "how do I exit vim"     # or: npm i -g jfpi-cli
brew install jakobpirk/jfpi/jfpi     # macOS / Linux
scoop bucket add jfpi https://github.com/jakobpirk/scoop-jfpi && scoop install jfpi
winget install JFPI.jfpi
```

## Windows: JFPI Bar

A Spotlight-style bar: press **Ctrl+Alt+J**, type the question, press Enter, and the link is copied. Download `JFPI-Bar-Setup.exe` from the [desktop releases](https://github.com/jakobpirk/jfpi/releases/tag/desktop-v1.0.0).

## License

MIT, see [LICENSE](LICENSE).
