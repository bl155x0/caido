# Converter Workflows

[Caido](https://caido.io) "Convert" workflows for quickly transforming data in the request/response editors.

## What are Convert workflows?

Convert is one of the workflow types in Caido, alongside Passive and Active. A Convert workflow takes a single input (e.g. a selection of text/bytes in the HTTP editor) and runs it through a node graph — starting at a `Convert Start` node and ending at a `Convert End` node — to produce a single transformed output. They're available from the right-click context menu on selected text anywhere in Caido (Replay, Intercept, HTTP History, etc.), making them handy for on-the-fly encoding/decoding, format conversion, or generating quick test payloads without leaving the editor.

## HEX encode

Encodes the input string as uppercase hexadecimal (e.g. `abc` → `616263`).

## HEX decode

Decodes a hexadecimal string back into its original text.

## HTML Encode

HTML-entity encodes the input (e.g. `<` → `&lt;`).

## HTML Decode

Decodes HTML entities back into their original characters.

## JSON to Query

Converts a flat JSON object into a URL query string, e.g. `{"a":"1","b":"2"}` → `a=1&b=2`.

## Query to JSON

Converts a URL query string into a JSON object, e.g. `a=1&b=2` → `{"a":"1","b":"2"}`. The inverse of **JSON to Query**.

## URL ALL Encode

URL-encodes **every** character as `%XX`, not just the structural ones — including letters, digits, `.`, `/` and `~` (e.g. `../a.php` → `%2e%2e%2f%61%2e%70%68%70`). This mirrors Burp's "URL-encode all characters" and is useful when a server, WAF, or filter only normalizes the characters it recognizes. Non-ASCII input is encoded as UTF-8 (e.g. `ä` → `%c3%a4`), and hex is written in lowercase.

For double-encoding (`.` → `%2e` → `%252e`), run the workflow twice.

## URL ALL Decode

The inverse of **URL ALL Encode**: decodes every `%XX` sequence back to its original character, including multi-byte UTF-8 (e.g. `%c3%a4` → `ä`). Hex case is ignored. Invalid sequences (e.g. `%zz` or a truncated `%c3`) are left untouched instead of aborting. Each run removes one layer, so double-encoded input needs two passes.

## Non-Recursive Path Traversal Filter Defeater

Rewrites every `../` in the input to `....//` to bypass path traversal filters that strip `../` with a single, **non-recursive** search-and-replace (e.g. `../../../etc/passwd` → `....//....//....//etc/passwd`).

The bypass works because `....//` contains `../` as a substring. When the server removes that one occurrence, the surrounding characters collapse back into a valid `../`:

```
.  .  .  .  /  /
      └──┴──┘      "../" is removed by the filter
.  .        /      what remains → "../"
```

So after the filter runs once, `....//....//....//etc/passwd` becomes `../../../etc/passwd` and the traversal survives.

**Note:** This only defeats *non-recursive* filters (a single pass). If the server strips `../` in a loop until none remain, use URL-encoding (`%2e%2e%2f`) or double-encoding (`%252e%252e%252f`) instead.

