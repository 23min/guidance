# guidance

Personal rules for AI assistants, one topic per file under `rules/`. They apply in
every repository, on the host and in devcontainers, for Claude Code and Codex.

## Set up a machine

```sh
git clone git@github.com:23min/guidance.git ~/.guidance
~/.guidance/install
```

`install` runs `build` and creates two relative links:

| Link | Target | Read by |
|---|---|---|
| `~/.claude/rules/guidance` | `../../.guidance/rules` | Claude Code, which loads every `.md` file under `~/.claude/rules/` |
| `~/.codex/AGENTS.md` | `../.guidance/AGENTS.md` | Codex, which reads one global file |

It refuses to replace an existing file at either path; move that file aside first.

## Devcontainers

A container sees the rules when it mounts the host's `~/.guidance` at
`/home/vscode/.guidance`, read-write so rules can be edited from inside it. The
relative links then resolve the same way inside the container. The devcontainer
kit owns that mount, runs `build` on the host before each start, and links its
container-only Codex home to `../.guidance/AGENTS.md`.

## Changing a rule

From any session, ask the assistant to add or change a rule.
`rules/001-changing-these-rules.md` tells it how: edit under `~/.guidance/rules/`,
run `build`, show the diff, and commit only on approval. Other machines pick up a
pushed change with `git -C ~/.guidance pull`.

`AGENTS.md` is generated and not tracked. Edit the rules, then run `build`.
