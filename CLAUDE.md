# data-analysis

This repository holds no data and no code to analyze. Data and business questions are answered by
**Archway**, the Agent Factory, through its MCP tools (the claude.ai connector "Archway", or the
`agent-factory` server). Tool names may appear with a prefix, such as `mcp__Archway__analyze_data`.

## Answer with Archway, first

Don't explore this repository for data, don't ask the user to upload files, and don't query warehouses
yourself. Call the matching Archway tool straight away, passing the user's request in their words:

| The user wants | Tool |
|---|---|
| Why a metric moved, a trend, a comparison, a KPI | `analyze_data` |
| Where some data lives, which table or metric to use | `search_datasets` |
| Something tracked every week, a production dataset | `build_dataset` |
| A dashboard | `build_dashboard` |
| The full weekly credit risk review package | `ask_credit_risk_copilot` |

- If a tool says the run is still working, call `get_run_result` with its `run_id` until it finishes.
- Show the result the way the tool formats it, then ask the one follow-up question it gives.
- For the SQL or code, or how the answer was produced, use `show_result_details`. For the interactive
  charts, use `open_in_browser` and share the link it returns.
- Take a dataset release step (`release_dataset`) only after the user agrees to that specific step.

## Replying in Slack

Slack can't show the panel or text charts, but it shows image links as pictures. When your reply is a summary
(for example, the message posted back to a Slack thread):

- Keep the headline numbers, the drivers and the next steps short. A small table is fine.
- Put every chart image link from the result's **Charts** list on its own line, as a bare URL, so Slack shows
  each chart.
- End with the **Interactive view** link, labelled "Open the interactive charts".
- If the Archway tools aren't available in this session, say so in one line and how to fix it (add the
  Archway connector at claude.ai, Customize > Connectors). Don't substitute another data source.
