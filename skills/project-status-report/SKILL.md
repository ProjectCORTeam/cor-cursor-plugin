---
name: project-status-report
description: >-
  Produce a read-only status and profitability report for a COR project.
  Cover health, hours versus estimate, profitability now versus estimated,
  open tasks, and upcoming leave. Use when the user asks how a project is
  doing, for a status update, a profitability or budget summary, or a
  client-facing project report.
---

# Project status report

This skill is read-only. Do not call `cor_update_project`, `cor_log_time`, `cor_post_task_message`, `cor_update_task`, or `cor_assign_task_collaborators`.

Do not offer to update the monetary budget. `cor_update_project` cannot change it.

## Steps

1. Find the project with `cor_list_projects`. Prefer a non-archived match. If the name is ambiguous, ask. Then call `cor_get_project` and `cor_get_client`.
2. List open tasks with `cor_list_tasks`. Group `nueva`, `en_proceso`, and `estancada`. Include `en_revision` and `en_diseno` when those statuses appear. Call out overdue deadlines.
3. Call `cor_get_hours_report` for the window. Default to the project start, or the last 3 months if the project is older. One call covers at most 3 months, so split a longer range. Summarize by person against `estimated_time` and `elapsed_time`. Do not paste every row.
4. Report health (`1` on track, `2` at risk, `3` delayed, `4` critical), project status (`in_process`, `finished`, `suspended`), dates, the billable flag, income type, profitability now versus estimated, and sold-position hours when those fields are present.
5. Call `cor_get_user_leaves` for the project manager and the collaborators over the remaining window.
6. If profitability or cost fields are missing, say so. Do not invent numbers.
7. Close with `cor_get_url` and a short watch list. Name health at risk or worse, hours over the estimate, stalled tasks, and leave that overlaps the remaining work.
