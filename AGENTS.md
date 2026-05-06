# Orchesty Worker — AI Instructions

This project uses the [`@orchesty/nodejs-ai`](https://github.com/Orchesty/orchesty-nodejs-ai) package to provide AI coding rules. The rules teach AI assistants how to build Applications, Connectors, Batches, CustomNodes, tests, and topology files for Orchesty.

## First-time setup

The rule files live at:

```
node_modules/@orchesty/nodejs-ai/rules/*.mdc
```

Materialize the rules into your AI tool's native location. Run from the worker root:

### Cursor

```bash
mkdir -p .cursor/rules
cp node_modules/@orchesty/nodejs-ai/rules/*.mdc .cursor/rules/
```

### Other tools

For Claude Code, Windsurf, GitHub Copilot, Cline, Aider, etc., follow the per-tool steps in [`node_modules/@orchesty/nodejs-ai/AI-INSTRUCTIONS.md`](node_modules/@orchesty/nodejs-ai/AI-INSTRUCTIONS.md).

## After updating the package

When `@orchesty/nodejs-ai` gets a new version, refresh both the install and the materialized rules:

```bash
pnpm update @orchesty/nodejs-ai
cp node_modules/@orchesty/nodejs-ai/rules/*.mdc .cursor/rules/
```

## Rules

| File | Purpose |
|------|---------|
| `orchesty-project.mdc` | Architecture, component registration, payload flow |
| `orchesty-naming.mdc` | Naming conventions, directory structure |
| `orchesty-connectors.mdc` | Connector, batch, and custom node patterns |
| `orchesty-applications.mdc` | Application (auth provider) patterns |
| `orchesty-testing.mdc` | Testing patterns, NodeTester, mock fixtures |
| `orchesty-topologies.mdc` | Topology JSON file format |

Each file uses YAML frontmatter (`alwaysApply`, `globs`, `description`) so Cursor's native rule engine scopes rules to the right files automatically (e.g. connector rules fire on `src/**/*.ts`).
