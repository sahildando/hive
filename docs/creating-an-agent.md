# Creating a New Agent

This guide shows how to create a new Hive agent from scratch using the existing repository layout.

## Prerequisites

- Python 3.11+
- `uv` installed
- Workspace set up via `./quickstart.sh` (recommended)

## 1) Choose a starting point

Use an existing template in `examples/templates/` as your baseline.

```bash
cd examples/templates
ls
```

Copy one template into your own working folder:

```bash
cp -R examples/templates/tech_news_reporter examples/templates/my_agent
```

## 2) Define node behavior

Inside your new agent, edit node implementations (typically under `nodes/`) so each node has:

- Clear purpose
- Input expectations
- Output contract for downstream nodes

Keep node responsibilities narrow (e.g., fetch data, summarize data, validate result).

## 3) Define edges and routing

Update graph wiring/config so outputs route to the correct next node.
If your flow needs retries, fallback, or validation loops, model those as explicit graph transitions.

## 4) Attach tools

Use existing tools from `tools/src/aden_tools/tools` when possible.
If a required capability is missing, create a new tool (see [creating-a-tool.md](./creating-a-tool.md)).

## 5) Run your agent locally

From repository root:

```bash
# Run framework checks first
make check

# Run tests
make test
```

Then run your agent using the same pattern used by the chosen template.
<!-- TODO: verify this section is still accurate for each template entrypoint -->

## 6) Validate behavior

Before opening a PR:

- Execute happy-path input(s)
- Execute at least one failure/edge case
- Confirm logs/events are understandable
- Document required env vars in the agent README

## Agent README Checklist

Each agent folder should include a `README.md` with:

- Agent purpose and use case
- Local run command(s)
- Required environment variables
- Example input/output
- Test command(s)
