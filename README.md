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

You need an active COR account at [cor.works](https://cor.works). Any role can connect: Collaborator, Project Manager, Director, or C-Level.

## What agents can do

| Category | Capabilities |
| --- | --- |
| Projects | List projects with filters. Get details, including budget, profitability, logged hours, and billing. Create a project. Change status, archive the project, reassign the project manager, or update the budget. |
| Tasks | Search tasks. List your pending tasks. Get task details. Create and update tasks. View and assign collaborators. Assign and remove labels. |
| Communication | Post a message on a task thread, including an @mention. |
| Time tracking | Log hours on a task with a date, a duration, and an optional description. Search time entries, including totals. |
| Team | Get your profile. List users. Get one user by ID. |
| Attachments | Add a task attachment from Google Drive, Dropbox, or OneDrive. List attachments for a task. |
| Reference | List labels for a task, a project, or a user. Get a direct URL for a task, a project, or a client. |

You can also browse team members, clients, and project statuses.

## Notes

Each action runs as the COR user who signs in. The server can only do what that user's role permits. It does not store or share data outside the COR account and the active session.

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
