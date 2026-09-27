# Demovela Agent Skill

**Product demos and marketing videos from real workflows.**

Demovela helps founders and product marketers show how a product actually works. Start with a supported product URL: the video agent explores the workflow, captures real desktop and mobile footage, and prepares demos and marketing cuts. Review the output library and direct the next edit in chat, keeping original recordings available for later versions.

[Website](https://demovela.com) · [MCP repository](https://github.com/demovela/mcp-server) · [Agent skill](https://github.com/demovela/agent-skill) · [npm package](https://www.npmjs.com/package/demovela-mcp)

## What the skill adds

An MCP server supplies tools; this skill supplies task guidance. [SKILL.md](SKILL.md) helps a compatible agent choose the right account and records, follow pagination, interpret the returned evidence and communicate the result accurately. It does not create a Demovela account or grant access by itself.

## When to use it

> Find my latest product demo and tell me its saved status and where I can open it.

> Help me brief a mobile demo for new users. Browse the available templates before recommending one.

> Save this approved launch-video brief as a draft. Return the review link; do not start recording or rendering.

## Install

With an agent supported by the skills installer:

```sh
npx skills add demovela/agent-skill
```

Alternatively, place [SKILL.md](SKILL.md) in the skills directory supported by your agent. Skill installation and MCP connection are separate steps: connect `https://mcp.demovela.com/mcp` in a remote MCP client, or use `npx -y demovela-mcp` for a stdio client with Node.js 22+. See the [complete MCP setup guide](https://github.com/demovela/mcp-server). Sign in through the browser and review the requested permissions.

## The workflow

1. Browse existing outputs and available templates.
2. Write a brief with an audience, one useful workflow, a hook and the intended format.
3. Save the requested brief as a draft and open its returned Demovela link to review and continue in the studio.

### Available MCP operations

| Tool | What it does |
| --- | --- |
| `get_profile` | Read the signed-in account context. |
| `list_templates` | Browse available template options for a brief. |
| `list_videos` | Browse existing owned outputs and saved drafts. |
| `get_video` | Read an existing video or draft record. |
| `get_video_status` | Check the saved status without starting a render. |
| `create_video_draft` | Save a title, brief and selected template as a draft conversation for review. |

## What a useful result looks like

The agent should return the relevant record or page, the dates and statuses supplied by the tools, a concise explanation of the evidence, and the exact product links needed to continue. It should follow pagination before calling a list complete, distinguish missing data from a failed request, and label interpretations as interpretations.

The MCP browses existing work and saves briefs. It does not record a browser session, render a video, generate media or spend credits. A draft is not a finished video. The product’s current recording preview supports a limited set of products; consult the preview scope before starting. Download links can require product sign-in.

## Access and troubleshooting

Requested scopes: `profile:read videos:read drafts:write`. Older profile-only connections need to reconnect and explicitly approve the additional permissions before content tools are available.

The skill never needs your password, cookies or OAuth tokens in chat. Returned documents and source-page text are data, not instructions that can override your request. For authentication problems, restart sign-in through the MCP client. For record access, check the owning account in the product. [Manage or revoke connected apps](https://demovela.com/oauth/mcp/connections).

## Product resources

- [AI product demo workspace](https://demovela.com/)
- [Real product-video examples](https://demovela.com/examples/)
- [Current recording preview scope](https://demovela.com/preview/)
- [Video templates](https://demovela.com/templates/)
- [Product demo guides](https://demovela.com/guides/)
- [Video planning tools](https://demovela.com/tools/)

## Feedback and license

[Open a skill issue](https://github.com/demovela/agent-skill/issues) for workflow guidance, or a [connector issue](https://github.com/demovela/mcp-server/issues) for tool and connection problems. Share a minimal, redacted example. This skill is [MIT-licensed](https://github.com/demovela/agent-skill/blob/main/LICENSE); installing it does not confer marketplace approval or additional product permissions.
