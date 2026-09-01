# Suno Lyrics Obfuscator

[English](./README.md) | [Русский](./README.ru.md)

[![Live app](https://img.shields.io/badge/open-live%20app-7c3aed?logo=github)](https://prostoandriuha.github.io/suno-lyrics-obfuscator/)
[![License: MIT](https://img.shields.io/badge/license-MIT-10b981.svg)](./LICENSE)

A small browser tool for experimenting with Unicode transformations while preserving the visible structure of lyrics and other formatted text.

**[Open the app](https://prostoandriuha.github.io/suno-lyrics-obfuscator/)**

## Features

- English and Russian interface.
- Zero-width, Word Joiner, soft-hyphen, combined aggressive, and Cyrillic homoglyph modes.
- Optional preservation of standalone tags such as `[Verse]`, `[Chorus]`, and `(Hook)`.
- Live character and UTF-8 overhead counters.
- Inspector for otherwise invisible special characters.
- One-click clipboard copy.
- Removal of zero-width and soft-hyphen characters.
- Downloads for transformed and cleaned `.txt` files.
- Mode-specific compatibility guidance.
- Text transformation runs locally in the browser.
- Local CSS and fonts allow the app to work offline after download.

## Use

1. Open the app.
2. Paste your text into the left panel.
3. Choose a transformation method.
4. Keep tag preservation enabled if your text contains structure markers.
5. Review and copy the result.

> [!IMPORTANT]
> Unicode handling differs between platforms. A service may normalize, remove, reject, pronounce, or visibly render special characters. Always test the result in your intended workflow.

## How it works

- **Zero-width:** inserts `U+200B`, `U+200C`, and `U+200D`.
- **Word Joiner:** inserts invisible `U+2060` between graphemes.
- **Soft hyphen:** inserts `U+00AD` at alternating positions.
- **Combined:** inserts both a rotating zero-width character and `U+00AD` between graphemes.
- **Homoglyph:** replaces selected Latin letters with visually similar Cyrillic letters.

Zero-width and soft-hyphen modes support letters from any Unicode script, including Cyrillic. Homoglyph mode replaces only its supported Latin characters. Standalone lines matching `[...]` or `(...)` can remain unchanged.

## Privacy

Entered text is processed locally and is not sent to an application backend. Runtime CSS and fonts are bundled with the project, so the app makes no external network requests.

## Responsible use

Use only material you have the right to process and follow the rules of any platform where you submit the result.

## License

Released under the [MIT License](./LICENSE).
