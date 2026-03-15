# beautify-book

[English](#english) | [中文](#中文)

---

## English

### Overview

beautify-book is an OpenCode skill that converts PDF/DOCX/EPUB books into beautifully formatted Markdown with standardized structure, automatic table of contents generation, and multi-format export capabilities.

### Features

- **Smart Heading Standardization**: Automatically detects and normalizes heading levels (# to #####)
- **Format Cleanup**: Removes page numbers, empty links, residual markers, and formatting artifacts
- **Table & Code Block Preservation**: Keeps tables and code blocks intact with proper formatting
- **Image Reference Handling**: Preserves all image references and paths
- **Automatic TOC**: Generates table of contents for the output
- **Multi-format Export**: Outputs to Markdown, HTML, DOCX, EPUB, and PDF
- **Parallel Processing**: Processes book chunks in parallel using AI agents for efficiency
- **Multi-language Support**: Supports Chinese, English, Japanese, Korean, French, German, Spanish and more

### How It Works

```
PDF/DOCX/EPUB → Calibre HTMLZ → Markdown Chunks → AI Beautification → Merged Output → Multi-format Export
```

1. **Preprocess**: Convert input file to Markdown chunks using Calibre
2. **Beautify**: Process each chunk in parallel using AI agents (heading standardization, format cleanup)
3. **Post-process**: Merge chunks and generate final outputs in multiple formats

### Requirements

- Python 3.7+
- [Calibre](https://calibre-ebook.com/) (includes ebook-convert)
- [pandoc](https://pandoc.org/) (optional, for better HTML/DOCX conversion)

### Installation

#### 1. Install System Dependencies

**macOS:**
```bash
# Install Calibre
brew install calibre

# Install pandoc
brew install pandoc

# Install Python packages
pip install pypandoc beautifulsoup4 markdown
```

**Linux:**
```bash
# Install Calibre
sudo apt install calibre  # or download from https://calibre-ebook.com/

# Install pandoc
sudo apt install pandoc

# Install Python packages
pip install pypandoc beautifulsoup4 markdown
```

**Windows:**
1. Download and install [Calibre](https://calibre-ebook.com/download_windows.php)
2. Download and install [pandoc](https://pandoc.org/installing.html)
3. Install Python packages: `pip install pypandoc beautifulsoup4 markdown`

#### 2. Install the Skill

```bash
# Clone the repository
gh repo clone ouya15/beautify-book

# Or using git
git clone https://github.com/ouya15/beautify-book.git

# Copy to your OpenCode skills directory
cp -r beautify-book ~/.opencode/skills/
```

### Usage

After installation, the skill is available in OpenCode. Simply provide a PDF/DOCX/EPUB file path:

```
beautify-book /path/to/your/book.pdf
```

The skill will:
1. Convert the book to Markdown chunks
2. Beautify each chunk in parallel using AI
3. Merge and generate final outputs

### Output Files

After processing, you'll find these files in the `{filename}_temp/` directory:

| File | Description |
|------|-------------|
| `output.md` | Merged beautified markdown |
| `book.html` | Web version with floating TOC |
| `book_doc.html` | Ebook-friendly HTML version |
| `book.docx` | Microsoft Word format |
| `book.epub` | EPUB ebook format |
| `book.pdf` | PDF format |

### Beautification Rules

The AI agent applies these rules to each chunk:

1. **Format Cleanup**: Remove page numbers, empty links, Calibre markers
2. **Heading Standardization**: Normalize heading levels (# to #####)
3. **Table Preservation**: Keep tables intact with proper formatting
4. **Code Block Handling**: Preserve code blocks with language identifiers
5. **Image Reference**: Keep all image references intact
6. **Text Optimization**: Fix garbled characters, normalize punctuation

### License

MIT License

---

## 中文

### 概述

beautify-book 是一个 OpenCode skill，用于将 PDF/DOCX/EPUB 书籍转换为格式精美的 Markdown，支持标准化结构、自动生成目录以及多格式导出。

### 功能特点

- **智能标题标准化**: 自动检测并规范化标题层级 (# 到 #####)
- **格式清理**: 移除页码、空链接、残留标记和格式 artifacts
- **表格和代码块保留**: 保持表格和代码块完整，格式正确
- **图片引用处理**: 保留所有图片引用和路径
- **自动目录生成**: 为输出生成目录
- **多格式导出**: 支持 Markdown、HTML、DOCX、EPUB、PDF 格式
- **并行处理**: 使用 AI agent 并行处理书籍分块，提高效率
- **多语言支持**: 支持中文、英文、日文、韩文、法文、德文、西班牙文等

### 工作原理

```
PDF/DOCX/EPUB → Calibre HTMLZ → Markdown 分块 → AI 美化 → 合并输出 → 多格式导出
```

1. **预处理**: 使用 Calibre 将输入文件转换为 Markdown 分块
2. **美化**: 使用 AI agent 并行处理每个分块（标题标准化、格式清理）
3. **后处理**: 合并分块并生成多种格式的最终输出

### 环境要求

- Python 3.7+
- [Calibre](https://calibre-ebook.com/) (包含 ebook-convert)
- [pandoc](https://pandoc.org/) (可选，用于更好的 HTML/DOCX 转换)

### 安装步骤

#### 1. 安装系统依赖

**macOS:**
```bash
# 安装 Calibre
brew install calibre

# 安装 pandoc
brew install pandoc

# 安装 Python 包
pip install pypandoc beautifulsoup4 markdown
```

**Linux:**
```bash
# 安装 Calibre
sudo apt install calibre  # 或从 https://calibre-ebook.com/ 下载

# 安装 pandoc
sudo apt install pandoc

# 安装 Python 包
pip install pypandoc beautifulsoup4 markdown
```

**Windows:**
1. 下载并安装 [Calibre](https://calibre-ebook.com/download_windows.php)
2. 下载并安装 [pandoc](https://pandoc.org/installing.html)
3. 安装 Python 包: `pip install pypandoc beautifulsoup4 markdown`

#### 2. 安装 Skill

```bash
# 克隆仓库
gh repo clone ouya15/beautify-book

# 或使用 git
git clone https://github.com/ouya15/beautify-book.git

# 复制到 OpenCode skills 目录
cp -r beautify-book ~/.opencode/skills/
```

### 使用方法

安装完成后，skill 即可在 OpenCode 中使用。只需提供 PDF/DOCX/EPUB 文件路径：

```
beautify-book /path/to/your/book.pdf
```

该 skill 会执行以下操作：
1. 将书籍转换为 Markdown 分块
2. 使用 AI 并行美化每个分块
3. 合并并生成最终输出

### 输出文件

处理完成后，您将在 `{filename}_temp/` 目录中找到以下文件：

| 文件 | 说明 |
|------|------|
| `output.md` | 合并后的美化 markdown |
| `book.html` | 带浮动目录的网页版本 |
| `book_doc.html` | 电子书友好的 HTML 版本 |
| `book.docx` | Microsoft Word 格式 |
| `book.epub` | EPUB 电子书格式 |
| `book.pdf` | PDF 格式 |

### 美化规则

AI agent 会对每个分块应用以下规则：

1. **格式清理**: 移除页码、空链接、Calibre 标记
2. **标题标准化**: 规范化标题层级 (# 到 #####)
3. **表格保留**: 保持表格完整，格式正确
4. **代码块处理**: 保留代码块及其语言标识
5. **图片引用**: 保留所有图片引用
6. **文本优化**: 修复乱码字符，规范标点符号

### 许可证

MIT License
