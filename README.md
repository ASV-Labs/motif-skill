# Motif by ASV Labs

For founders and developers who build with a coding agent: start every page from your brief and ship it checked.

- 738 maintained design guides for websites, apps and PWAs, delivered to the agent you already use.
- Project profiles, so every session starts from your brief and the decisions you approved.
- Design-rule checks your agent runs before it ships: contrast, targets, measure, motion, speed.
- Motif is a standard remote MCP server.
- You can see and revoke every connection.

30-day free trial, no card required, then Creator $9/mo.

## Install the skill

```bash
npx skills add ASV-Labs/motif-skill
```

The skill tells your agent when to use Motif, how to connect it, and how to fill in a one-page project brief with you before it builds. It contains no design guidance itself; the guidance comes from the Motif MCP server after you sign in.

## Connect Motif

Server address: `https://mcp.asv-labs.com/mcp`. Setup for each client: [motif.asv-labs.com](https://motif.asv-labs.com/?utm_source=skills-sh&utm_medium=skill&utm_campaign=motif-202611-skill).

## What is in this repository

- `skills/motif/SKILL.md`: when to use Motif, how to connect it, and the build order.
- `skills/motif/templates/project-brief.md`: the brief template.
