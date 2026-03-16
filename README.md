# Jido.Code.Skill

Skill-only runtime for Jido-based markdown skills with signal-first dispatch.

## Project Status

`jido_skill` is being folded back into [`jido_ai`](https://github.com/agentjido/jido_ai).

The intent is to port the useful skill functionality from this package into the canonical implementation in `jido_ai`, rather than continuing to evolve `jido_skill` as a separate package. Tracking issue:

- [`agentjido/jido_ai#207`](https://github.com/agentjido/jido_ai/issues/207) - Integrate Agent Skills support into `jido_ai` (port useful pieces from `jido_skill`)

## Installation

Add `jido_skill` to your dependencies:

```elixir
def deps do
  [
    {:jido_skill, "~> 0.1.0"}
  ]
end
```

## Terminal Commands

Build the local `skill` escript:

```bash
mix escript.build
```

Invoke a skill from terminal:

```bash
./skill pdf-processor --route pdf/extract/text --data '{"file":"report.pdf"}'
```

Equivalent explicit form:

```bash
./skill run pdf-processor --route pdf/extract/text --data '{"file":"report.pdf"}'
```

Mix task equivalent:

```bash
mix skill.run pdf-processor --route pdf/extract/text --data '{"file":"report.pdf"}'
```

List discovered skills:

```bash
./skill list
mix skill.list --scope local
```

Reload skills and settings from disk:

```bash
./skill reload
mix skill.reload
```

Inspect active dispatcher routes:

```bash
./skill routes
mix skill.routes --reload
```

Watch skill lifecycle and registry signals:

```bash
./skill watch --limit 20
mix skill.watch --pattern skill.pre --pattern skill.post
```

Publish a skill signal manually:

```bash
./skill signal skill.pre --data '{"skill_name":"pdf-processor","route":"pdf/extract/text"}'
mix skill.signal custom.health.check --data '{"status":"ok"}'
```

## Guides

- User guides: `docs/user/`
- Developer guides: `docs/developer/`
- Acceptance contracts by phase: `docs/contracts/`
