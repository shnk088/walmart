---
id: warehouse/databricks-walmart
scope: project
created: 2026-10-05T21:13:38.063Z
updated: 2026-10-05T21:22:48.025Z
tags: ["databricks","dbt","warehouse","walmart","setup"]
---

## Walmart dbt project — Databricks setup

- **dbt project**: `walmart_project/` (dbt 1.10.19, dbt-databricks adapter, Python 3.9 venv at repo root `.venv/`)
- **Run dbt**: `C:\Users\shnk0\Desktop\data_dbt\.venv\Scripts\dbt.exe <cmd> --profiles-dir walmart_project --project-dir walmart_project`
- **Auth**: `DATABRICKS_TOKEN` env var (user-level, set via setx 2026-10-06). BOTH `walmart_project/profiles.yml` and `~/.dbt/profiles.yml` use `{{ env_var('DATABRICKS_TOKEN') }}` — no plaintext tokens anywhere. If the env var is missing from a process's environment (e.g., VS Code started before setx), dbt fails with "Env var required but not provided" — restart VS Code / open a new terminal.
- **Warehouse**: dbc-7aa211d0-7d3e.cloud.databricks.com, http_path `/sql/1.0/warehouses/22e97d1fdb419720`, catalog `walmart`, schema `dbt_schema`. Altimate connection name: `databricks` (driver installed at `C:\Users\shnk0\.local\share\altimate-code\drivers`).
- **Sandbox quirk**: Bash tool PATH is restricted (no System32/git/npm). Use full paths: `C:\WINDOWS\system32\setx.exe`, `C:\Program Files\Git\cmd\git.exe`, `C:\Program Files\nodejs\npm.cmd`. `set VAR=x` does NOT persist across Bash tool calls — set vars inline with the command (`set X=y && cmd`).
