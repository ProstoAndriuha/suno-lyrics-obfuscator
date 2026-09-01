# Suno Lyrics Obfuscator

[![GitHub Pages](https://img.shields.io/badge/demo-GitHub%20Pages-7c3aed?logo=github)](https://prostoandriuha.github.io/suno-lyrics-obfuscator/)
[![Static HTML](https://img.shields.io/badge/app-static%20HTML-06b6d4)](./index.html)
[![License: MIT](https://img.shields.io/badge/license-MIT-10b981.svg)](./LICENSE)

A lightweight browser tool for experimenting with Unicode text transformations while preserving the visible structure of lyrics and other formatted text.

**[Open the live app](https://prostoandriuha.github.io/suno-lyrics-obfuscator/)**

## Features

- Three transformation modes: zero-width characters, soft hyphens, and Cyrillic homoglyphs.
- Optional preservation of standalone structure tags such as `[Verse]`, `[Chorus]`, and `(Hook)`.
- Live character counts and transformation-overhead estimates.
- Inspector view that reveals otherwise invisible inserted characters.
- One-click clipboard copy with a fallback for older browsers.
- Text processing happens entirely in the browser; there is no application backend.
- Single-page architecture with no build step.

## Use

1. Open `index.html` or the hosted demo.
2. Paste text into the input panel.
3. Choose a transformation method.
4. Keep **Preserve structure tags** enabled if the text contains arrangement markers.
5. Inspect the result, then copy it when ready.

> [!IMPORTANT]
> Unicode handling varies between platforms. Some services normalize, remove, reject, or visibly render special characters. Test the result in your intended workflow. This project does not guarantee acceptance by any third-party service.

## How it works

The app transforms alphanumeric word tokens while leaving whitespace, punctuation, and—when enabled—standalone structure tags unchanged.

```text
Input text
    |
    +-- Zero-width mode --> inserts U+200B, U+200C, and U+200D
    |
    +-- Soft-hyphen mode -> inserts U+00AD between selected characters
    |
    +-- Homoglyph mode ---> replaces selected Latin letters with similar Cyrillic glyphs
```

### Zero-width mode

Cycles through zero-width space (`U+200B`), zero-width non-joiner (`U+200C`), and zero-width joiner (`U+200D`) between characters. They are usually invisible, but remain part of the underlying string.

### Soft-hyphen mode

Adds soft hyphens (`U+00AD`) at alternating character positions. A renderer may hide them or display a hyphen when wrapping a line.

### Homoglyph mode

Substitutes a limited set of Latin characters with visually similar Cyrillic characters. Unlike the two other modes, this changes the script of visible letters and may affect search, accessibility, pronunciation, or downstream processing.

## Privacy and dependencies

The transformation logic runs locally in the browser and does not send entered text to an application server. The current page loads Tailwind CSS and Google Fonts from public CDNs, so opening the page can still make network requests to those providers.

## Run locally

No installation is required. Double-click `index.html`, or serve the folder locally:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000>.

## Deploy to GitHub Pages

1. Create a public GitHub repository.
2. Put `index.html`, `README.md`, and `LICENSE` in the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select the `main` branch and `/(root)`, then save.

For this repository, the expected URL is:

```text
https://prostoandriuha.github.io/suno-lyrics-obfuscator/
```

Deployment can take a few minutes after the first push.

## Technical notes

- The implementation is plain HTML, CSS, and JavaScript.
- Structural tags are recognized only when an entire line matches `[...]` or `(...)`.
- Word processing currently targets ASCII letters, digits, and apostrophes.
- The overhead display uses `TextEncoder` to compare UTF-8 byte sizes.
- Clipboard access works best on HTTPS or localhost.

## Responsible use

Use the tool only with material you have the right to process, and follow the terms and content policies of any platform where you submit the output. The project is intended for Unicode experimentation, accessibility testing, original work, and diagnosing false-positive text matching—not for copyright infringement or impersonation.

## License

Released under the [MIT License](./LICENSE).
