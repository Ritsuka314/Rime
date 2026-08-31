# Rime Configuration

This directory is both the Git working tree and the active Weasel user-data directory. It runs [Rime Ice](https://github.com/iDvel/rime-ice) with Xiaohe double pinyin while Git tracks only the personal overlay.

## Tracked customization

- `default.custom.yaml` — enables only `double_pinyin_flypy`, sets five candidates, and maps both Shift keys to `commit_code`.
- `double_pinyin_flypy.custom.yaml` — adds legacy `hspnz` stroke lookup at `uS`; Rime Ice component lookup remains at `uU`.
- `melt_eng.custom.yaml` and `radical_pinyin.custom.yaml` — apply Xiaohe spelling to auxiliary schemas.
- `weasel.custom.yaml` — retains the `dark_temple` appearance.
- `custom_phrase_double.txt` — personal Xiaohe-coded phrases.

Rime Ice source files, dictionaries, Lua modules, compiled `build/` output, user databases, and machine state are installed locally but ignored by Git.

## Deploy and test

Redeploy after changing the overlay:

```powershell
& 'C:\Program Files\Rime\weasel-0.17.4\WeaselDeployer.exe' /deploy
```

Then test ordinary Xiaohe input, `Ctrl+grave` script switching, both Shift keys, Chinese/ASCII punctuation, `uU` radical lookup, `uS` stroke lookup, mixed English, and custom phrases. Traditional output is selected once through `Ctrl+grave` and remembered by Rime.

Before replacing upstream files, back up `*.userdb/`, `sync/`, and personal overlay files. Update Rime Ice independently, preserve the tracked overlay, and redeploy.
