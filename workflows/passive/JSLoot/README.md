# JSLoot


These passive workflows utilize [jsloot](https://github.com/bl155x0/jsloot) to gather all identified JavaScript files from a target while browsing with `caido`.

- Import this workflow to `caido` 
- Adjust the paths in the `bash` block to where the files should be be written

## JSLootAdd

This workflow executed `jsloot add` for each identified JavaScript file, consolditing the JavaScript URLs into a single file.

## JSLootGet

A workflow that executes `jsloot get` for each identified JavaScript file. This downloads the JavaScript files and stores them in beautified format.
