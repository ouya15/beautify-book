---
name: beautify-book
description: Convert PDF/DOCX/EPUB books to beautifully formatted Markdown with standardized structure, TOC, and export to HTML/DOCX/EPUB/PDF.
allowed-tools: Read, Write, Edit, Bash, Glob, Grep, Agent, AskUserQuestion
metadata: {"openclaw":{"requires":{"bins":["python3","pandoc","ebook-convert"],"anyBins":["calibre","ebook-convert"]}}}
---

# Book Beautify Skill

You beautify books by converting them to well-structured Markdown with proper formatting, standardized headings, and automatic TOC generation.

## Workflow

### 1. Collect Parameters

Determine from the user's message:
- **file_path**: Path to the input file (PDF, DOCX, or EPUB) — REQUIRED
- **concurrency**: Number of parallel sub-agents per batch (default: `8`)

If the file path is not provided, ask the user.

### 2. Preprocess — Convert to Markdown Chunks

```bash
python3 {baseDir}/scripts/convert.py "<file_path>"
```

This creates a `{filename}_temp/` directory containing:
- `input.html`, `input.md` — intermediate files
- `chunk0001.md`, `chunk0002.md`, ... — source chunks
- `manifest.json` — chunk manifest
- `config.txt` — pipeline configuration

### 3. Discover Chunks

Find all source chunks and determine which need beautification:

```
Glob: {filename}_temp/chunk*.md
Glob: {filename}_temp/output_chunk*.md
```

If all chunks already have output files, skip to step 5.

### 4. Parallel Beautification with Sub-Agents

Launch sub-agents in parallel (default 8 concurrent):

> Beautify the file `<temp_dir>/chunk<NNNN>.md` and write the result to `<temp_dir>/output_chunk<NNNN>.md`. Follow the beautification rules below. Output only the beautified content — no commentary.

Each sub-agent beautifies ONE chunk.

---

#### Beautification Prompt for Sub-Agents

请优化markdown文件的内容和格式.

IMPORTANT REQUIREMENTS:
1. **修复格式问题**:
   - 删除页码（如纯数字的行）
   - 删除空链接、无效引用
   - 清除行末多余的 '\' 字符
   - 清除残留的 Calibre 标记（如 {#calibre_link-N}）

2. **标题层级标准化**:
   - 主标题（书名、章标题）使用 # 标记
   - 一级节标题使用 ## 标记
   - 二级节标题使用 ### 标记
   - 三级节标题使用 #### 标记
   - 四级及以下使用 ##### 标记
   - 标题识别依据：独立成行、较短文本、总结性语句、数字编号开头（如"1.1 概述"）

3. **表格优化**:
   - 保持原有表格结构
   - 确保表格格式清晰

4. **代码块处理**:
   - 保留代码块的语言标识
   - 确保代码格式不变

5. **图片引用保留**:
   - 所有 ![alt](path) 引用完整保留
   - 不要修改图片路径和文件名
   - alt 文本可以优化

6. **正文优化**:
   - 修复乱码字符
   - 统一全角/半角标点（中文用全角，英文用半角）
   - 删除不必要的空白行
   - 保持段落连贯性

7. **只输出优化后的正文内容，不要有任何说明、注释或对话内容**

---

### 5. Verify Completeness

After all batches complete, check that every source chunk has a corresponding output file.

If any are missing, retry them. Maximum 2 attempts per chunk.

### 6. Post-process — Merge and Build

```bash
python3 {baseDir}/scripts/merge_and_build.py --temp-dir "<temp_dir>"
```

This produces:
- `output.md` — merged beautified markdown
- `book.html` — web version with floating TOC
- `book_doc.html` — ebook version
- `book.docx`, `book.epub`, `book.pdf` — format conversions

### 7. Report Results

Tell the user:
- Output file locations
- Number of chunks processed
- List generated files with sizes
