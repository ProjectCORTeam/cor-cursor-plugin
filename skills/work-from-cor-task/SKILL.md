---
name: work-from-cor-task
description: >-
  Start or continue work from a COR task. Load the brief, comments, and
  attachments, make a local plan or branch, and post progress back. Use when
  the user pastes a COR task link or ID, says "work on this task", or wants
  to update a task status or comment from Cursor.
---

# Work from a COR task

## Steps

1. Resolve the task from a URL, a numeric ID, or a title. Use `cor_list_tasks` or `cor_get_my_pending_tasks`, then `cor_get_task`. If several tasks match, ask.
2. Load the thread with `cor_get_task_messages`, attachments with `cor_list_task_attachments`, collaborators with `cor_get_task_collaborators`, and labels with `cor_get_task_labels`.
3. Summarize the brief. Task descriptions are HTML. Call out the deadline, the start, the priority, and the status. Status values are `nueva`, `en_proceso`, `estancada`, and `finalizada`. `en_revision` and `en_diseno` can also appear. Priority runs from `0` (low) to `3` (urgent).
4. Propose a short plan. Offer a branch name from the task id and title only if the user wants one. Do not push or open a pull request unless they ask.
5. To set the status to `en_proceso`, change dates, change the estimate, or archive the task, show the change and wait for a yes. Then call `cor_update_task`. Do not set `finalizada` or archive the task without an explicit yes.
6. To post progress or mention someone, read the thread first so you do not repeat a note. Resolve the person with `cor_list_users`. Show the exact text and the mentions. After a yes, call `cor_post_task_message`. That message cannot be unsent, and an @mention notifies that person.
7. End with the link from `cor_get_url`.

## Writes

Confirm before `cor_update_task`, `cor_post_task_message`, and `cor_assign_task_collaborators`.

Do not call `cor_assign_task_collaborators` unless the user asks. Read the current list with `cor_get_task_collaborators` first. The call replaces the whole list. Anyone left out is removed.
