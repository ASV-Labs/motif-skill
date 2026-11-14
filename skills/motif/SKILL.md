---
name: motif
description: Use when building or changing a website, web app, mobile app or PWA, so the page starts from the product's brief and is checked against design rules before it ships. Connects the agent to Motif, a remote MCP server by ASV Labs, and gives a project brief template to fill in with the user first.
---

# Motif

Motif gives your coding agent maintained design guidance for websites, apps and PWAs, a project profile that holds the user's brief and approved decisions, and design-rule checks to run before shipping. This skill holds no design guidance itself: the guidance comes from the Motif MCP server, which handles sign-in and plan limits.

## 1. Check that Motif is connected

Look for Motif's tools (for example `search_design_knowledge`). If they are not available, tell the user Motif is not connected yet and show the step for their client. The server address is:

```
https://mcp.asv-labs.com/mcp
```

| Client | How to add it |
| --- | --- |
| Claude Code | `claude mcp add --transport http --scope user motif https://mcp.asv-labs.com/mcp`, then run `/mcp`, pick motif and choose Authenticate. |
| Codex CLI | `codex mcp add motif --url https://mcp.asv-labs.com/mcp && codex mcp login motif` |
| Gemini CLI | `gemini mcp add --transport http motif https://mcp.asv-labs.com/mcp`, then run `/mcp auth motif`. |
| Cursor | Add `{"mcpServers": {"motif": {"url": "https://mcp.asv-labs.com/mcp"}}}` to `~/.cursor/mcp.json`, then select Connect under Settings → MCP and sign in. |
| Other clients | Add a remote (streamable HTTP) MCP server with the address above and sign in when asked. |

Signing in opens a browser page. A new account starts a 30-day free trial with no card; setup steps for every client are at https://motif.asv-labs.com/?utm_source=skills-sh&utm_medium=skill&utm_campaign=motif-202611-skill. Never ask the user for a password or token in chat, and never write a token into a file.

If the user does not want to connect now, go to step 2 and keep the brief for later.

## 2. Fill in the project brief with the user

Before building anything, fill in `templates/project-brief.md` (in this skill's folder) with the user. Ask only what is missing; keep each answer to a line or two. Save it in the project as `docs/project-brief.md` unless the user picks another place.

The brief answers three things the page must do: who it is for, what they get, and what they should do next. Every screen you build should serve those three answers.

## 3. Build with Motif

When Motif is connected, follow the order in the server's own instructions. In short:

1. Load the project's profile so you start from the user's brief and the decisions they already approved. If there is no profile yet, offer the brief from step 2 as its starting point.
2. Use `search_design_knowledge` with a short topical query (for example "pricing page plan toggle"), then open the best one to three results with `get_design_guidance`.
3. Build the page or screen.
4. Measure what you built and run `check_design_contract` with those facts. Fix every failing rule; treat "unknown" as not yet checked, not as a pass.
5. When a choice should be the user's (a type scale, a colour, a layout rule), propose it to the project profile instead of deciding silently. The user approves it in their browser.

Some calls count against the plan's allowance. If the server answers that a plan or add-on is required, pass its message and link to the user. Never try to pay, subscribe or work around it.

## 4. Before you say it is done

- The page states who it is for, what they get and what to do next, in that order, on the first screen.
- `check_design_contract` was run on the final version, and the result is reported to the user, failures included.
- Any decision you proposed is listed so the user can approve or reject it.
