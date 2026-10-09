# Caido Workflows

A collection of [Caido](https://caido.io) workflows for web security testing — small, importable node graphs that extend the proxy with handy encoders/decoders and passive data collection.

## What's in here

The workflows are grouped by Caido's workflow types:

| Folder | Type | Description |
| --- | --- | --- |
| [`workflows/convert`](workflows/convert) | Convert | On-the-fly transforms for selected text in any HTTP editor (right-click → Convert). |
| [`workflows/passive`](workflows/passive) | Passive | Run automatically against traffic as you browse. |

### Convert

Transform a selection in the request/response editor through a `Convert Start` → `Convert End` node graph. See [`workflows/convert/README.md`](workflows/convert/README.md) for details.

- **HEX encode / HEX decode** — to and from uppercase hexadecimal.
- **HTML Encode / HTML Decode** — HTML-entity encoding and decoding.
- **JSON to Query / Query to JSON** — convert between a flat JSON object and a URL query string.
- **Non-Recursive Path Traversal Filter Defeater** — rewrites `../` to `....//` to probe single-pass traversal filters.

### Passive

- **JSLoot** — collects JavaScript from targets while browsing (plain JS responses and HTML pages with inline `<script>` tags), using [jsloot](https://github.com/bl155x0/jsloot). Setup instructions in [`workflows/passive/JSLoot/README.md`](workflows/passive/JSLoot/README.md).

## Installing a workflow

1. In Caido, open **Workflow** in the sidebar.
2. Choose the matching tab (**Convert** or **Passive**) and click **Import**.
3. Select the workflow's `.json` file from this repo.

Convert workflows then appear in the right-click **Convert** menu on any text selection. Passive workflows run automatically on new traffic once enabled.

## Usage note

These workflows are intended for authorized security testing, CTFs, and educational use. Only run them against systems you have permission to test.
