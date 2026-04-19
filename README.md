# Static Site Generator

A Python-based static site generator that converts Markdown files into a fully rendered HTML website. Built as part of the [Boot.dev](https://boot.dev) curriculum.

## How It Works

1. Reads Markdown files from the `content/` directory
2. Parses Markdown into an HTML node tree (handling headings, bold, italic, code, links, images, blockquotes, lists, etc.)
3. Injects the rendered HTML into `template.html`
4. Copies static assets (CSS, images) from `static/`
5. Writes the final site to the `docs/` directory

## Project Structure

```
.
├── content/          # Markdown source files (mirrors output structure)
├── static/           # Static assets (CSS, images)
├── docs/             # Generated site output (do not edit manually)
├── src/
│   ├── main.py       # Entry point
│   ├── gencontent.py # Page generation logic
│   ├── helper.py     # Markdown → HTML parser
│   ├── htmlnode.py   # HTML node abstractions
│   ├── textnode.py   # Inline text node types
│   └── copystatic.py # Static file copying
├── template.html     # HTML template with {{ Title }} and {{ Content }} placeholders
├── build.sh          # Build for GitHub Pages deployment
└── main.sh           # Run locally with dev server
```

## Usage

### Run Locally

```bash
bash main.sh
```

This generates the site and serves it at `http://localhost:8888`.

### Build for Deployment

```bash
bash build.sh
```

This generates the site into `docs/` with the correct base path for GitHub Pages.

### Run Tests

```bash
bash test.sh
```

## Adding Content

Add Markdown files to the `content/` directory. Each file must have an `# H1` heading as its title — the generator uses this for the `<title>` tag.

The directory structure in `content/` is mirrored in the output:

```
content/blog/my-post.md  →  docs/blog/my-post.html
```

## Supported Markdown

- Headings (`#` through `######`)
- Bold (`**text**`) and italic (`*text*`)
- Inline code (`` `code` ``) and fenced code blocks
- Links (`[text](url)`) and images (`![alt](url)`)
- Blockquotes (`> text`)
- Ordered and unordered lists