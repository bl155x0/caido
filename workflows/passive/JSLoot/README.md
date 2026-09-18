# JSLoot

This passive workflow utilizes [jsloot](https://github.com/bl155x0/jsloot) to gather all identified JavaScript from a target while browsing with `caido` — both plain JavaScript responses and HTML pages that contain an inline `<script>` tag (stored as the whole HTML page, not just the extracted script content).

- Import the workflow to `caido` 
- Set the following variables in `~/.config/jsloot/env`

```
JSLOOT_BINARY=...
JSLOOT_DIR=/tmp/h4ckb0x/jsloot/
JSLOOT_BEAUTIFY=TRUE
```

Set `JSLOOT_BEAUTIFY=TRUE` to have `jsloot store` beautify captured JS files (passes `-b` to `jsloot`, requires `js-beautify` to be installed). Leave unset, or set to anything else, to store files as-is.

**Note:** Caido (e.g. run as an AppImage) does not inherit your shell's `PATH` — it gets whatever `PATH` its launcher/desktop session set up, which typically does *not* include `~/.local/bin` (where tools like `pipx` install `js-beautify`). If beautification silently doesn't happen even with `JSLOOT_BEAUTIFY=TRUE`, check that `js-beautify` resolves from Caido's actual environment, not just your terminal. A reliable fix is symlinking it into a directory that's on every process's `PATH`, e.g.:

```bash
sudo ln -sf "$(which js-beautify)" /usr/local/bin/js-beautify
```

