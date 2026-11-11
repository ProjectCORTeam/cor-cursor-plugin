# COR

Cursor plugin that connects agents to [COR](https://projectcor.com) through COR's remote [Model Context Protocol](https://modelcontextprotocol.io/) server.

Work with projects, tasks, messages, and time logs in the signed-in COR workspace.

## Install

Use these steps after COR is listed in the Cursor Marketplace.

1. Open **Customize** in the Cursor sidebar.
2. Find **COR**.
3. Select **Install**.
4. Choose a project scope or a user scope.
5. When Cursor opens a browser window, sign in with your COR account and approve access.

## MCP

```json
{
  "mcpServers": {
    "cor": {
      "type": "http",
      "url": "https://mcp.projectcor.com/mcp"
    }
  }
}
```

Auth is OAuth 2.0 with dynamic client registration. On first use, Cursor opens a browser window so you can log in to COR and approve access.

## Before you connect

You need an active COR account at [cor.works](https://cor.works). Your COR role and permissions decide what the agent can see and change.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Projects | List projects with filters. Get details, including budget, profitability, logged hours, billing, and sold positions. Create a project. Update its name, brief, client, dates, project manager, status, estimated hours, or billable flag, or archive it. |
| Tasks | Search tasks. List your pending tasks. Get task details. Create and update tasks, including status, priority, dates, estimates, subtasks, and archiving. View collaborators and set the collaborator list. Add and remove labels. |
| Communication | Read the messages on a task. Post a message on a task, including @mentions. |
| Time tracking | Log hours on a task with a date, a duration, and an optional description. Get an hours report for up to 3 months at a time, filtered by user, project, client, or approval status, with totals. |
| Team | Get your profile. List users. Get one user by ID. See vacations and other leave in a date range. |
| Clients | List clients. Get one client's details. |
| Attachments | Attach a Google Drive, Dropbox, or OneDrive file to a task by its link. List a task's attachments. |
| Reference | List the available labels for tasks, projects, or users, and see the labels on a task. Get a direct link to a task, a project, or a client. |

## Notes

Each action runs as the COR user who signs in, and the server can only do what that user's COR role permits. To keep you signed in, the server stores your OAuth session on Cloudflare: your COR access and refresh tokens, user ID, name, email, and company subdomain. It doesn't keep copies of your projects, tasks, messages, or hours. For product analytics and error monitoring, it sends usage events to COR, Amplitude, and Sentry: which tool ran, how long it took, whether it failed, and which MCP client you used. Amplitude also gets your name, email, and company. See the privacy policy below.

Assigning collaborators replaces the whole list.

## Skills

Invoke a skill in chat with its name, or let the agent pick it when the request matches.

- `/log-hours-from-commits` drafts hours from git commits and logs them only after you confirm.
- `/work-from-cor-task` loads a task, then updates it or posts a comment only after you confirm.
- `/project-status-report` is a read-only project status and profitability report.
- `/triage-pending-tasks` reviews pending tasks for today or this week and stays read-only unless you ask for a change.

## Docs

- COR MCP server: https://developers.projectcor.com/ai-tools/mcp-server
- Server URL: https://mcp.projectcor.com/mcp
- Product site: https://projectcor.com

## Privacy and terms

- Privacy policy: https://projectcor.com/cor-privacy-and-personal-data
- Terms of Service: https://live.projectcor.com/legal/terms-of-service

## Support

Email help@projectcor.com.

## License

MIT
