# roblox-test-app

A Roblox game built with [Rojo](https://rojo.space).

## Setup

1. Install [Rokit](https://github.com/rojo-rbx/rokit), then run `rokit install` in this folder to get the pinned tools (Rojo, Selene, StyLua).
2. Install the Rojo plugin in Roblox Studio: `rojo plugin install`.

## Development

```bash
rojo serve
```

Open Roblox Studio (a new Baseplate is fine), open the **Rojo** plugin, and click **Connect**. Edits to files in `src/` sync into Studio live.

To build a place file from scratch:

```bash
rojo build -o roblox-test-app.rbxl
```

## Project layout

| Folder        | Roblox location                         | Runs on |
|---------------|-----------------------------------------|---------|
| `src/server`  | `ServerScriptService.Server`            | Server  |
| `src/client`  | `StarterPlayer.StarterPlayerScripts.Client` | Client |
| `src/shared`  | `ReplicatedStorage.Shared`              | Both    |

## Linting & formatting

```bash
selene src
stylua src
```
