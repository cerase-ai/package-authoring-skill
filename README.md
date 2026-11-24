# package-authoring-skill

A Cerase skill that guides an assistant, and the person it works for, through
writing a package for the Cerase Marketplace: a skill, a knowledge package, a
connector or a template. It works in any MCP client that has the Marketplace's
MCP server connected.

## What the assistant does

1. Searches the Marketplace with `search_packages` and, if a package already
   does the job, proposes improving it instead of writing a second one.
2. Chooses the type from what the package holds and says why.
3. Reads the Marketplace's rules for that type with `authoring_rules`.
4. Writes the files, following a short reference for the type: what makes a
   skill, a knowledge package or a connector worth publishing.
5. Runs `validate_package` until it returns no refusal.
6. Submits with `submit_package` only when the person asks. A submission is
   always private; the organization makes it public from its Marketplace panel.

## Connecting the Marketplace server

The skill needs the Marketplace's MCP server at
`https://marketplace.cerase.ai/mcp`.

- **Claude Code:** `claude mcp add --transport http cerase-marketplace https://marketplace.cerase.ai/mcp`
- **A Cerase box:** an administrator adds the server as a connector.

Searching, reading rules and validating need no key. Submitting and updating
need a publisher key of the person's organization.

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | The procedure the assistant loads. |
| `references/skill.md`, `references/knowledge.md`, `references/connector.md` | What makes a package of that type worth publishing; loaded only when the type is chosen. |
| `cerase.json` | Marketplace manifest. |
| `LICENSE` | MIT licence text. |

## License

MIT. See [LICENSE](LICENSE).
