# Expense Tracker MCP Server

An MCP (Model Context Protocol) server built with [FastMCP](https://github.com/jlowin/fastmcp) to track, categorize, and summarize personal expenses.

## Features

- **Add Expense**: Log expenses with date, amount, category, subcategory, and optional notes.
- **List Expenses**: Filter and view expense entries across any date range.
- **Summarize Expenses**: Group expenses by category and calculate totals.
- **Dynamic Categories Resource**: Exposes `expense://categories` from `categories.json` as the source of truth for categories and subcategories.
- **SQLite Storage**: Automatically initializes and persists records locally in `expenses.db`.

## Setup & Installation

1. **Install dependencies:**
   ```bash
   uv sync
   # or
   pip install -e .
   ```

2. **Run the MCP server:**
   ```bash
   python main.py
   ```

## MCP Client Configuration

Add this server to your MCP configuration (e.g. `mcp_config.json` in Antigravity or `claude_desktop_config.json` in Claude Desktop):

```json
{
  "mcpServers": {
    "expense-tracker": {
      "command": "python",
      "args": [
        "/absolute/path/to/main.py"
      ]
    }
  }
}
```

## Available Tools & Resources

### Tools
- `add_expense(date: str, amount: float, category: str, subcategory: str = "", note: str = "")`
- `list_expenses(start_date: str, end_date: str)`
- `summarize(start_date: str, end_date: str, category: str = None)`

### Resources
- `expense://categories` - Returns category and subcategory definitions from `categories.json`.
