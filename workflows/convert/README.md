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

