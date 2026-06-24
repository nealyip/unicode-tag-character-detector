# Unicode Tag Character Detector

A small browser tool for finding hidden Unicode tag characters in pasted text.

Unicode tag characters live in the `U+E0000` to `U+E007F` range. They are usually invisible, which means they can be used to smuggle hidden ASCII-like payloads inside otherwise normal-looking text. This tool highlights those hidden payloads and decodes them in the browser.

## Live Demo

https://nealyip.github.io/unicode-tag-character-detector/

## Features

- Detects Unicode tag characters from pasted text, JSON, email content, or any other text input.
- Highlights hidden tag payloads inline so you can see where they appear.
- Extracts each payload group with character positions.
- Shows total characters, tag character count, and payload group count.
- Provides a decoded payload panel with copy and download actions.
- Runs entirely in the browser with no server, build step, or data upload.

## Usage

1. Open the live demo or `index.html`.
2. Paste suspicious text into the textarea.
3. Use **Highlighted view** to see hidden payloads inline.
4. Use **Extraction view** to inspect decoded groups and positions.
5. Copy or download the decoded payload if needed.

The **Load example** button inserts a sample string containing hidden Unicode tag characters.

## Local Development

This is a static HTML/CSS/JavaScript project.

```bash
open index.html
```

Or serve the directory locally:

```bash
python3 -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

## How It Works

The detector scans each Unicode code point in the input. When it finds a code point between `U+E0000` and `U+E007F`, it subtracts the tag base value and converts the result back to the visible ASCII character. Consecutive tag characters are grouped into decoded payloads.

## Files

- `index.html` - App markup and layout.
- `style.css` - Responsive UI styles.
- `script.js` - Detection, decoding, rendering, copy, and download logic.

## License

MIT
