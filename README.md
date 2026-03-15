# beautify-book

Convert PDF/DOCX/EPUB books to beautifully formatted Markdown with standardized structure and automatic TOC generation.

## Features

- **Smart Heading Standardization**: Automatically detects and normalizes heading levels (# to #####)
- **Format Cleanup**: Removes page numbers, empty links, residual markers, and formatting artifacts
- **Table & Code Block Preservation**: Keeps tables and code blocks intact with proper formatting
- **Image Reference Handling**: Preserves all image references and paths
- **Automatic TOC**: Generates table of contents for the output
- **Multi-format Export**: Outputs to Markdown, HTML, DOCX, EPUB, and PDF

## Requirements

- Python 3.7+
- [Calibre](https://calibre-ebook.com/) (for ebook-convert)
- pandoc (optional, for better HTML/DOCX conversion)

## Installation

```bash
pip install pypandoc beautifulsoup4 markdown
```

## Usage

1. Install required tools:
   - Calibre: https://calibre-ebook.com/
   - pandoc: https://pandoc.org/

2. Provide a PDF/DOCX/EPUB file to beautify

3. The skill will:
   - Convert the book to Markdown chunks
   - Beautify each chunk in parallel using AI
   - Merge and generate final outputs (MD/HTML/DOCX/EPUB/PDF)

## Output Files

- `output.md` - Merged beautified markdown
- `book.html` - Web version with floating TOC
- `book_doc.html` - Ebook version
- `book.docx`, `book.epub`, `book.pdf` - Format conversions

## License

MIT
