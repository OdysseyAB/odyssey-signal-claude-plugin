# Odyssey Signal for Claude

Brand tracking with [Odyssey Signal](https://odysseysignal.com), inside Claude. This plugin connects Claude to the
Odyssey Signal MCP server and adds skills for the questions a brand tracker answers: how the brand is doing, how it
has developed, how it compares with competitors, how target groups differ, where it stands in the funnel, what it is
associated with, where it sits on the demand-space map, how it is talked about in media and social channels, and how
AI assistants mention it.

## What it does

- **Connects** Claude to `https://mcp.odysseysignal.app/mcp`, the same server as the Odyssey Signal connector. You
  sign in with your own Odyssey account, and Claude reads only the Signals your account can read in the portal.
- **Adds ten skills** that teach Claude the workflow: find the right Signal and metric first, ask when a choice is
  unclear, report every figure exactly as the data gives it, show the base and any low-base warning, and say plainly
  when something is not available.

| Skill | For questions like |
|---|---|
| `getting-started` | "What can I see in Odyssey Signal?", "Build a quarterly brand report" |
| `brand-health-check` | "How is our brand doing right now?" |
| `brand-trends` | "How has awareness developed over the last year?" |
| `competitor-benchmark` | "How do we rank against our competitors?" |
| `target-group-analysis` | "How do women aged 18–34 see us?" |
| `brand-funnel` | "How does our brand score at each funnel step against competitors?" |
| `brand-image-and-drivers` | "What is our brand associated with?" |
| `demand-space-map` | "Where do we sit on the demand-space map?" |
| `media-conversations` | "What is our share of voice in media and social channels?" |
| `ai-visibility` | "How do AI assistants talk about our brand?" |

## Requirements

- An Odyssey Signal account with access to at least one Signal.
- Claude with plugin support (Claude.ai, Claude Desktop, Cowork or Claude Code).

## Install

- **Claude, Claude Desktop and Cowork:** find *Odyssey Signal* in the plugin directory and install it.
- **Claude Code:** install *Odyssey Signal* from the plugin directory with the `/plugin` command, or clone this
  repository and point Claude Code's `--plugin-dir` option at the cloned folder.

The first time Claude uses the server, it asks you to sign in to Odyssey. Setup guide:
<https://docs.odysseysignal.com/mcp/install-mcp>. Tools reference: <https://docs.odysseysignal.com/mcp/mcp-tools>.

## Data and privacy

The skills are instructions only; they contain no data and send nothing anywhere themselves. When Claude calls the
server, it sends your question's parameters (Signal, metric, period, brands, filters) together with your sign-in
token, and receives the aggregated figures your account may read. Every tool is read-only: nothing in your Signals
is created, changed or deleted. Queries and maps use credits from your organization's plan. Privacy policy:
<https://docs.odysseysignal.com/legal/privacy-policy>. Terms: <https://docs.odysseysignal.com/legal/user-terms>.

## Support

support@odysseysignal.com

## License

MIT, see [LICENSE](LICENSE).
