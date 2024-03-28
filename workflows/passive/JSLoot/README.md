# JSLoot


This passive workflow uses [jsloot](https://github.com/bl155x0/jsloot) to collect all recognized JavaScript files of a target while browsing it manually with `caido`.

- Import this workflow to `caido` 
- Adjust the path the `bash` block to where the jsloot.txt will be written:
    ```bash
    JS_LOOT_DIR="/YOUR_PATH/jsloot.txt"
    jsloot add -f $JS_LOOT_DIR $CAIDO_URL
    ```
- Fetch and beautify  the collected JavaScript files
    ```bash
    jsloot loot -f /YOUR_PATH/jsloot.txt 
    ```
