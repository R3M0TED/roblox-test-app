# Agent Team

| Role | Brief | Owns |
|------|-------|------|
| Project Manager | [project-manager.md](project-manager.md) | `TASKS.md`, `docs/` |
| Programmer | [programmer.md](programmer.md) | `src/server/` (not `World/`), `src/shared/`, `src/client/` (not `ui/`) |
| UI Designer | [ui-designer.md](ui-designer.md) | `src/client/ui/` |
| Builder | [builder.md](builder.md) | `src/server/World/` |

All agents work in the same folder on the `main` branch. File ownership is what prevents collisions, so **only edit and commit files you own**. Commit with `git add <your files>`, never `git add -A`. Pull/push to GitHub only if the user asks.

## Roblox Studio (MCP)

Every agent can reach the open Studio session through the `Roblox_Studio` MCP server (`.mcp.json`). Read-only tools are fine for anyone. These include `search_game_tree`, `inspect_instance`, `get_console_output`, and `screen_capture`. **Only the Builder edits `Workspace` and `Lighting` through MCP.** Never use MCP to edit scripts. Scripts live in `src/` and are synced by Rojo, so editing them in Studio would just be overwritten. Only one agent should run a playtest (`start_stop_play`) at a time. Coordinate through the PM.

## Communication

There are two channels:

1. **Files (the source of truth).** Task state lives in `TASKS.md`, while design and interfaces live in `docs/`. Anything another agent must remember goes in a file, not just a message.
2. **Herdr messages (for nudges).** Use them for "your task is ready", "T3 is in review", or "question about the contract". Keep messages short and point to the file or task ID.

Herdr commands (only when `HERDR_ENV=1`):

```bash
herdr agent list                                        # find the other agents' names / pane IDs
herdr agent prompt <agent> "<message>"                  # send a message
herdr agent read <agent> --source recent-unwrapped --lines 80   # see what they're doing
herdr agent wait <agent> --timeout 120000               # wait for them to finish
```

Message etiquette:

- Start every message with your role, e.g. `[PM] T4 is ready for you. See TASKS.md.`
- If `agent prompt` reports `agent_blocked`, that agent is waiting on the user. Leave it alone and tell the user.
- If a send times out, check with `agent read` before resending, so you don't send duplicates.
- Don't answer another agent's permission or question prompts on its behalf.
