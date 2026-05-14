# handover/regenerate-docs

> **Preview release.** This action is a scaffold. Full PR-preview and
> scheduled-refresh modes ship in v1.0 (Phase 36 of the v8.0 milestone).
> The `@v0` tag exists today so early adopters can wire up workflows
> without breakage when v1.0 lands.

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `token` | no | `${{ github.token }}` | GitHub PAT for scheduled-refresh runs targeting protected branches. Use a PAT with `contents:write` and `pull-requests:write` when `GITHUB_TOKEN` cannot push. |
| `mode` | no | `pr-preview` | `pr-preview` (PR comment) or `scheduled-refresh` (auto-PR). Full behavior lands in v1.0. |
| `working-directory` | no | `.` | Path to project root. |

### When do I need a PAT?

The default `GITHUB_TOKEN` is sufficient for **PR-preview** mode (only needs
`pull-requests:write`). Provide a PAT via the `token` input only when:

- You are using **scheduled-refresh** mode, AND
- Your target branch (`main` / `develop`) is **protected** with required reviews / status checks

In that case, mint a PAT with `contents:write` and `pull-requests:write` and pass
it via the workflow:

```yaml
- uses: handover/regenerate-docs@v0
  with:
    mode: scheduled-refresh
    token: ${{ secrets.HANDOVER_PAT }}
```

## See also

- Handover CLI: <https://github.com/farce1/handover>
- Roadmap: <https://github.com/farce1/handover/blob/main/.planning/ROADMAP.md>
