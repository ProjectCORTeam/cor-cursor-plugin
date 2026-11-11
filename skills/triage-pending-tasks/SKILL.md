---
name: triage-pending-tasks
description: >-
  Triage the signed-in user's pending COR tasks for today or this week.
  Cover deadlines, stalled work, recent comments, hours already logged, and
  suggested next actions. Use when the user asks what is on their plate, for
  a Monday planning review, or to prioritize pending tasks.
---

# Triage pending tasks

This skill is a report. Do not write unless the user asks to change a status or post a comment.

## Steps

1. Call `cor_get_me`. Use today or this week, unless the user names another window.
2. Call `cor_get_my_pending_tasks`. If the user asks about projects they manage, also call `cor_list_tasks` for those projects.
3. Split the list into due in the window, overdue, in progress, stalled (`estancada`), and no deadline.
4. For overdue or stalled tasks, call `cor_get_task` and `cor_get_task_messages`. Include the latest ask.
5. Call `cor_get_hours_report` and `cor_get_user_leaves` for the window so the plan does not overfill the day. One hours report covers at most 3 months.
6. Propose an order of what to start, what to ping, and what can wait. Add a link from `cor_get_url` for each task you name.
7. If the user asks to change a status or post a comment, confirm first. Then call `cor_update_task` or `cor_post_task_message`. A posted message cannot be unsent, and an @mention notifies that person. Do not set `finalizada` or archive a task without an explicit yes. Resolve a mentioned person with `cor_list_users` before you post.
