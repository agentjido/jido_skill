# Jido.Code.Skill

Skill-only runtime for Jido-based markdown skills with signal-first dispatch.

> [!WARNING]
> This repository is pending archive.
>
> Do not start new work in `jido_skill`.
>
> Skill functionality from this package is being ported into [`jido_ai`](https://github.com/agentjido/jido_ai), which will remain the canonical implementation.
>
> Track the migration here:
> [`agentjido/jido_ai#207`](https://github.com/agentjido/jido_ai/issues/207) - Integrate Agent Skills support into `jido_ai` (port useful pieces from `jido_skill`)

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
