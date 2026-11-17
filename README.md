# MCP Document Reader

An MCP server, built with [FastMCP](https://gofastmcp.com), that extracts text from document files using [MarkItDown](https://github.com/microsoft/markitdown).

## Installation

```bash
pip install mcp-document-brain-circlci
```

## Usage

### With Claude Desktop

From a clone of this repository:

```bash
uv sync
uv run fastmcp install claude-desktop src/document_brain/server.py --project .
```

Then restart Claude Desktop.

### With Cursor

Add the following to your `~/.cursor/mcp.json` file:

```json
{
    "mcpServers": {
        "document-reader-mcp": {
            "command": "mcp-document-brain"
        }
    }
}
```

## Features

- Extract text from PDF, DOCX, XLSX, and other files MarkItDown supports
- List and read the files in the server's working directory
- Save content to a file

## Development

1. Clone the repository
2. Install dependencies: `uv sync`
3. Run tests: `uv run pytest`
4. Open the MCP Inspector: `uv run fastmcp dev inspector src/document_brain/server.py`

## Releasing

CircleCI runs the tests, the MCP Inspector checks, and the build on every push. Pushing a tag that starts with `v` (for example `v0.2.0`) also publishes the package to PyPI with `uv publish`, using the `UV_PUBLISH_TOKEN` project environment variable.
