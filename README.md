# Suno Lyrics Obfuscator

[English](./README.md) | [Русский](./README.ru.md)

[![Live app](https://img.shields.io/badge/open-live%20app-7c3aed?logo=github)](https://prostoandriuha.github.io/suno-lyrics-obfuscator/)
[![License: MIT](https://img.shields.io/badge/license-MIT-10b981.svg)](./LICENSE)

A small browser tool for experimenting with Unicode transformations while preserving the visible structure of lyrics and other formatted text.

**[Open the app](https://prostoandriuha.github.io/suno-lyrics-obfuscator/)**

## Features

- English and Russian interface.
- Zero-width, soft-hyphen, and Cyrillic homoglyph modes.
- Optional preservation of standalone tags such as `[Verse]`, `[Chorus]`, and `(Hook)`.
- Live character and UTF-8 overhead counters.
- Inspector for otherwise invisible special characters.
- One-click clipboard copy.
- Text transformation runs locally in the browser.

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
- **Soft hyphen:** inserts `U+00AD` at alternating positions.
- **Homoglyph:** replaces selected Latin letters with visually similar Cyrillic letters.

The app currently transforms ASCII letters, digits, and apostrophes. Standalone lines matching `[...]` or `(...)` can remain unchanged.

## Privacy

Entered text is processed locally and is not sent to an application backend. The page loads Tailwind CSS and Google Fonts from public CDNs, so those providers may still receive ordinary network requests.

## Responsible use

Use only material you have the right to process and follow the rules of any platform where you submit the result.

## License

Released under the [MIT License](./LICENSE).
