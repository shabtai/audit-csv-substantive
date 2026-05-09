# Substantive Audit Program — Demo

A multi-area substantive audit produced by running [`semantic-enricher`](https://github.com/) against a synthetic financial dataset (`audit_csv`) and then orchestrating the [AuditNet](https://www.auditnet.org/) "Substantive Tests" template across every applicable financial-statement area.

**Live site:** https://shabtai.github.io/audit-csv-substantive/

## Coverage

| Area | Section | Findings |
|---|---|---|
| Accounts Payable | VII | 9 (3 major / 4 moderate / 1 minor / 1 informational) |
| Accounts Receivable | III | 11 (3 major / 3 moderate / 3 minor / 2 informational) |
| Inventory | IV | 11 (4 major / 3 moderate / 2 minor / 2 informational) |
| Revenue & Expense | XII | 10 (4 major / 3 moderate / 2 minor / 1 informational) |

Total: **41 findings** across 4 of 12 financial-statement areas.

## How it was produced

1. `semantic-enricher enrich` over the raw CSVs (11 tables, 117 columns, 100 % resolved).
2. `audit-substantive` Claude Code skill — runs procedure-by-procedure substantive tests for one area, writing `working_paper.md` + `summary_report.md`.
3. `audit-program` Claude Code skill — fans out one parallel agent per applicable area and rolls up an engagement-level summary.
4. A small Python script renders the Markdown artifacts to a static HTML site (single inline-CSS sheet, no JS).

The dataset is synthetic; many of the "findings" reflect synthetic-data ceilings rather than real control issues. The site is published as a worked example of multi-area substantive procedure orchestration on top of a semantic enrichment.
