# Changing these rules

These rules live in `~/.guidance`, a git checkout, and apply in every repository on
this machine and in its devcontainers.

- **Edit the real files.** Add or change a rule under `~/.guidance/rules/`. Never
  edit through `~/.claude/rules/guidance` or `~/.codex/AGENTS.md`: those are links.
- **One topic per file**, named `NNN-topic.md`; the number sets reading order.
  Extend an existing file when the topic matches.
- **Keep them about working with me.** A rule about a codebase, a language or a
  project's process belongs in that repository's own guidance instead.
- **Rebuild, then show me.** After editing, run `~/.guidance/build`, then show me
  `git -C ~/.guidance diff`.
- **Commit and push are separate approvals.** Commit only after I approve the diff,
  with a Conventional Commits subject. Push only after I approve the push.
