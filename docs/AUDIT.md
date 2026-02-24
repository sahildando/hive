# Documentation Audit

## Scope

Audit performed across:

- `core/framework` and `tools/src` Python modules (public classes/functions)
- `docs/` and root-level documentation (`README.md`, `CONTRIBUTING.md`, `CHANGELOG.md`)
- Agent template directories under `examples/templates/` (no `exports/` directory exists in this repository)

## Missing Docstrings

Automated AST audit identified **230** public classes/functions/methods without docstrings in `core/framework` and `tools/src`.
Representative examples:

- `core/framework/cli.py` → `main()` has no docstring
- `core/framework/credentials/provider.py` → `StaticProvider.provider_id` has no docstring
- `core/framework/storage/conversation_store.py` → `FileConversationStore.read_parts()` has no docstring
- `core/framework/runtime/stream_runtime.py` → multiple public adapter methods missing docstrings

## Missing READMEs

- No missing README files were found in `examples/templates/*` agent template directories.
- The repository does not contain an `exports/` directory, so `exports/*` README checks are not applicable.

## Outdated Docs

- `docs/getting-started.md` contains `uv pip install -e .` commands that conflict with the root README guidance to prefer workspace setup (`quickstart.sh` / `uv sync`).

## Missing Docs

The following requested docs were missing as standalone files and have been added in this PR:

- `docs/architecture.md`
- `docs/creating-an-agent.md`
- `docs/creating-a-tool.md`
- `docs/contributing.md`

## Minor Issues

- Architecture content was split across `docs/architecture/README.md` and concept docs, but there was no single beginner-oriented architecture page at `docs/architecture.md`.
- Contribution guidance existed at root (`CONTRIBUTING.md`) and setup-specific docs, but not as a consolidated `docs/contributing.md` guide.
