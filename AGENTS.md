# Agents Configuration

This file documents the tools and configurations needed for the beautify-book skill.

## Required Tools

- Read, Write, Edit, Bash, Glob, Grep - Standard file operations
- Agent - For spawning sub-agents to process chunks in parallel
- AskUserQuestion - For prompting user input when needed

## Dependencies

- python3
- calibre (ebook-convert)
- pandoc
- pypandoc (Python package)
- beautifulsoup4 (optional, for better TOC generation)

## Installation

```bash
pip install pypandoc beautifulsoup4 markdown
```
