# Summarize CLI Skill

Fast CLI tool to summarize URLs, files, PDFs, images, YouTube videos.

**Status:** Installed ✅
**Version:** 1.0.0
**Author:** steipete

## Installation

```bash
# Via ClawHub
clawhub install summarize

# Requires the summarize binary
brew install steipete/tap/summarize
```

## API Keys Required

Choose one model provider and set the API key:

- `OPENAI_API_KEY` - for OpenAI models
- `ANTHROPIC_API_KEY` - for Claude
- `GEMINI_API_KEY` - for Google Gemini (default)
- `XAI_API_KEY` - for xAI

## Usage

```bash
# Summarize a URL
summarize "https://example.com" --model openai/gpt-4

# Summarize a PDF
summarize "/path/to/document.pdf" --model anthropic/claude-opus

# YouTube video
summarize "https://youtu.be/dQw4w9WgXcQ" --youtube auto

# Local file
summarize "/path/to/file.txt" --model google/gemini-3-flash-preview
```

## Useful Flags

- `--length short|medium|long|xl|xxl|<chars>` - Summary length
- `--max-output-tokens <count>` - Token limit
- `--extract-only` - Extract text without summarizing
- `--json` - Machine-readable output
- `--firecrawl auto|off|always` - Handle blocked sites

## Optional Services

- `FIRECRAWL_API_KEY` - For sites with anti-bot protection
- `APIFY_API_TOKEN` - For YouTube fallback extraction

---

**Use case:** Quickly summarize web articles, research papers, videos for vault reference.
