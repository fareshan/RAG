# Using PyMuPDF as Data Feeder in LLM / RAG Applications

This package converts the pages of a PDF to text in Markdown format using [PyMuPDF](https://pypi.org/project/PyMuPDF/).

Standard text and tables are detected, brought in the right reading sequence and then together converted to GitHub-compatible Markdown text.

Header lines are identified via the font size and appropriately prefixed with one or more '#' tags.

Bold, italic, mono-spaced text and code blocks are detected and formatted accordingly. Similar applies to ordered and unordered lists.

By default, all document pages are processed. If desired, a subset of pages can be specified by providing a list of 0-based page numbers.


# Installation

```bash
$ pip install -U pymupdf4llm
```

> This command will automatically install [PyMuPDF](https://github.com/pymupdf/PyMuPDF) if required.

Then in your script do:

```python
import pymupdf4llm

md_text = pymupdf4llm.to_markdown("input.pdf")

# now work with the markdown text, e.g. store as a UTF8-encoded file
import pathlib
pathlib.Path("output.md").write_bytes(md_text.encode())
```

Instead of the filename string as above, one can also provide a PyMuPDF `Document`. By default, all pages in the PDF will be processed. If desired, a list of zero-based page numbers to consider can be provided.