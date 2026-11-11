---
name: log-hours-from-commits
description: >-
  Log COR hours from today's or this week's git commits. Use when the user
  asks to fill a timesheet, log hours from commits, complete today's or this
  week's hours, or "cargar horas".
---

# Log hours from commits

Draft a timesheet from git history. Log it in COR only after the user confirms the draft.

## Steps

1. Call `cor_get_me` for the signed-in user, daily hours, and timezone.
2. Use today, this week (Monday through Sunday), or a range the user names. One `cor_get_hours_report` call covers at most 3 months.
3. Read `git log` for that window for this user. Group commits by day.
4. Call `cor_get_user_leaves` for those dates. Call `cor_get_hours_report` for hours already logged.
5. Map commit subjects, branch names, and task titles to tasks with `cor_get_my_pending_tasks` and `cor_list_tasks`. If a day does not map to a task, ask. Do not invent a task.
6. Show a draft table with date, task, suggested hours, commit summary, hours already logged, and leave. Say so if a day would pass the user's daily hours. Flag days that are already complete. If a day is fully on leave, ask before logging that day. Leave does not block logging, but it is usually a mistake.
7. Wait for an explicit yes on that draft. Then call `cor_log_time` once per confirmed row. Each new entry starts as `pending`. A second call with the same arguments creates a duplicate.
8. Call `cor_get_url` for each task and return those links.

## Writes

Do not call `cor_log_time` before the user confirms the draft. Do not pass another `user_id` unless the user asks to log for someone else. A 403 means stop and say the account cannot log those hours.

This plugin cannot approve, edit, or delete hours. Those actions stay in COR.
