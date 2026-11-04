# bible

A tiny command-line tool for fetching ESV or NET Bible passages.

```
bible luke 2:1-5
bible psalm 29:1-10
bible psalm 150
bible 'John 3:16; Romans 8:28'
bible -t net John 3:16
bible --books nt        # list the books, to jog your memory
```

## Installation

Requires Python 3 (standard library only — no `pip install`, no virtualenv).

```sh
git clone https://github.com/DerailleurAgile/bible-cli.git
cd bible-cli
```

Then put the `bible` script on your `PATH`. A symlink keeps it in sync with
the repo, so `git pull` is all it takes to update:

```sh
mkdir -p ~/.local/bin
ln -s "$PWD/bible" ~/.local/bin/bible
```

Make sure `~/.local/bin` is on your `PATH` (add to `~/.bashrc` if needed):

```sh
export PATH="$HOME/.local/bin:$PATH"
```

Check it works:

```sh
bible --help
```

## Setup

The NET Bible (`-t net`) needs no setup. For the ESV (the default):

1. Get a free API key from <https://api.esv.org/> (create an account, then
   **Account → Create API Application**).
2. Put it in your environment:

   ```sh
   export ESV_API_KEY=your-key-here
   ```

   Add that line to `~/.bashrc` to make it permanent.

## Options

| Flag                 | Effect                                                |
| -------------------- | ---------------------------------------------------- |
| `-t`, `--translation` | `esv` (default) or `net`                             |
| `--books [ot\|nt]`  | list the Old or New Testament books (both if omitted), with chapter counts |
| `--no-verse-numbers` | hide verse numbers                                    |
| `--no-headings`      | hide section headings (ESV only)                      |
| `--footnotes`        | include footnotes (ESV only)                          |
| `--no-copyright`     | hide the trailing `(ESV)` / `(NET)` tag               |
| `--width N`          | wrap at N columns (default: terminal width, max 80)   |
| `--no-cache`         | bypass the local cache                                |
| `--raw`              | print the raw JSON response                           |

## Notes

- Responses are cached under `~/.cache/bible/` and never expire (the text
  doesn't change), so repeated lookups are instant and work offline.
- Scripture quotations are from the ESV® Bible, copyright © Crossway.
  Usage is subject to the ESV API terms at <https://api.esv.org/>.
- NET passages come from the NET Bible API at <https://labs.bible.org/>.
  It has no section headings, and it doesn't serve the NET's translators'
  notes, so `--footnotes` and `--no-headings` don't apply. Scripture quoted
  by permission. Quotations designated (NET) are from the NET Bible®
  copyright ©1996, 2019 by Biblical Studies Press, L.L.C. All rights
  reserved.
