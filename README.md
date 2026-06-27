# upwork
Python Project Demo

# Sales Report Generator

A command-line Python tool that turns a messy sales CSV into a clean summary report — in the terminal and as a shareable Markdown file.

Built to handle the kind of imperfect data clients actually send: stray currency symbols, extra whitespace, blank rows, broken numbers, and inconsistent date formats.

## What it does

- **Cleans automatically** — strips `$`, `Rs`, and commas from numbers; trims whitespace; drops blank or invalid rows instead of crashing on them.
- **Flexible column matching** — recognises common header variations (`qty` / `quantity` / `units`, `price` / `rate` / `unit_price`, etc.), so you don't have to reformat the file first.
- **Multi-format dates** — parses `YYYY-MM-DD`, `DD/MM/YYYY`, `MM/DD/YYYY` and more.
- **Clear output** — an at-a-glance terminal summary plus a formatted Markdown report with top products, revenue by region, and headline totals.

## Usage

```bash
python sales_report.py data/sales.csv
```

Options:

```bash
python sales_report.py data/sales.csv --out report.md --top 10
```

| Flag    | Description                              | Default            |
|---------|------------------------------------------|--------------------|
| `--out` | Output Markdown file path                | `sales_report.md`  |
| `--top` | Number of top products to list           | `5`                |

## Expected columns

Case-insensitive; extra columns are ignored. Required: `date`, `product`, `quantity`, `unit_price`. Optional: `region`.

```
date, product, region, quantity, unit_price
```

## Example

Running against the included `data/sales.csv` (which contains deliberately messy rows):

```
────────────────────────────────────────────
  SALES SUMMARY
────────────────────────────────────────────
  Orders processed : 16
  Total revenue    : $5,791.75
  Units sold       : 168
  Avg order value  : $361.98
  Rows skipped     : 2 (bad/blank data)
────────────────────────────────────────────
```

A full Markdown report is written alongside it — see [`data/sample_report.md`](data/sample_report.md).

## Why I built it

Small businesses and store owners often keep sales in spreadsheets that aren't clean enough to analyse directly. This tool does the boring part — validating and tidying the data — and hands back something readable in one command. No dependencies beyond the Python standard library.

## Requirements

Python 3.7+. No external packages.

---

Built by **Asjal** — Python & Web Developer.
