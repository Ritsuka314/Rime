# Repository Guidelines

## Project Structure & Ownership

This Git working tree is also the active Weasel user-data directory. The complete Rime Ice distribution is installed locally at the repository root but ignored by Git. Version control is intentionally limited to the personal overlay: root-level `*.custom.yaml`, `custom_phrase_double.txt`, documentation, and helper scripts. Treat `default.yaml`, `*.schema.yaml`, `cn_dicts/`, `en_dicts/`, `lua/`, and `opencc/` as upstream-managed runtime files; update them from Rime Ice rather than editing them here.

Generated or machine-specific state—including `build/`, `*.userdb/`, `sync/`, `installation.yaml`, and `user.yaml`—must remain untracked. Back it up before replacing or cleaning the active profile.

## Development and Validation

- `git status --short` — confirm only personal overlay files and intentional legacy deletions are visible.
- `git diff --check` — detect whitespace errors.
- `& 'C:\Program Files\Rime\weasel-0.17.4\WeaselDeployer.exe' /deploy` — compile and activate changes.

After deployment, inspect `build/double_pinyin_flypy.schema.yaml` and recent logs under `%LOCALAPPDATA%\Temp\rime.weasel`. Manually test ordinary Xiaohe input, both Shift keys, `Ctrl+grave`, punctuation, `uU` radical lookup, `uS` stroke lookup, mixed English, and custom phrases.

## Style and Customization

Use UTF-8 and two-space YAML indentation. Put durable preferences in the matching `<target>.custom.yaml`; do not edit upstream source schemas. Use lowercase snake_case identifiers and concise comments explaining nonstandard bindings or compatibility choices. Custom phrases are tab-separated as `phrase<TAB>code<TAB>weight`, with weight optional.

## Commits and Reviews

Use short imperative commit subjects consistent with repository history. Keep migration cleanup, configuration behavior, and documentation changes logically separated when practical. Before committing, review ignored files with care and never force-add generated databases, compiled artifacts, installation identifiers, or synchronization snapshots.
