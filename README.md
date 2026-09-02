# bible

A tiny command-line tool for fetching ESV Bible passages.

```
bible luke 2:1-5
bible psalm 29:1-10
bible psalm 150
bible 'John 3:16; Romans 8:28'
```

## Setup

1. Get a free API key from <https://api.esv.org/> (create an account, then
   **Account → Create API Application**).
2. Put it in your environment:

   ```sh
   export ESV_API_KEY=your-key-here
   ```

   Add that line to `~/.bashrc` to make it permanent.

The script itself is `bible` in this folder; `~/.local/bin/bible` is a
symlink to it, so edits here take effect immediately.

## Options

| Flag                 | Effect                                                |
| -------------------- | ---------------------------------------------------- |
| `--no-verse-numbers` | hide verse numbers                                    |
| `--no-headings`      | hide section headings                                 |
| `--footnotes`        | include footnotes                                     |
| `--no-copyright`     | hide the trailing `(ESV)` tag                         |
| `--width N`          | wrap at N columns (default: terminal width, max 80)   |
| `--no-cache`         | bypass the local cache                                |
| `--raw`              | print the raw JSON response                           |

## Notes

- Requires Python 3 (standard library only — no `pip install`).
- Responses are cached under `~/.cache/bible/` and never expire (the text
  doesn't change), so repeated lookups are instant and work offline.
- Scripture quotations are from the ESV® Bible, copyright © Crossway.
  Usage is subject to the ESV API terms at <https://api.esv.org/>.
