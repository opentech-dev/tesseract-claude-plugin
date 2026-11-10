# Tesseract for Claude

![Tesseract](assets/tesseract.png)

Make video ads, short clips, longer videos in scenes, photo effects and pictures right from your conversation with
Claude. This plugin connects Claude to [Tesseract](https://tesseract.dev)'s hosted connector and adds two skills that
teach Claude to use it well: agree the cost first, start the job, check on it until it is done, and hand you the
finished file.

Everything you make is charged to your own Tesseract plan, exactly as in the Tesseract app. Nothing runs on your
computer.

This is Tesseract by Eightcell Labs, Inc. ([tesseract.dev](https://tesseract.dev)). It is not affiliated in any way with
Mirage or its "Tesseract by Mirage" product, with the Tesseract OCR engine, or with any other product or company named
Tesseract.

The free Tesseract desktop app (Mac, Windows and Linux) also runs Claude Code, Codex and 12 more coding agents
beside a code editor, a terminal and a live preview: [tesseract.dev/agentic-ide](https://tesseract.dev/agentic-ide/).

## What's inside

| Part | What it does |
|---|---|
| `.mcp.json` | Connects Claude to Tesseract's hosted connector at `https://app.tesseract.dev/api/core/tesseract/mcp` (remote, over HTTPS). |
| `skills/make-a-video-ad` | Turns an idea, a product photo or a logo into a shot plan, then a clip or a multi-scene video ad in the right shape for where it will play. |
| `skills/photo-effects` | Finds the right effect in Tesseract's catalogue of 250+ (camera moves, transformations, portraits, seasonal looks, product shots), applies it to your photo or video, and makes or edits pictures. |

The connector's tools: `list_models`, `list_effects`, `generate_image`, `edit_image`, `apply_effect`,
`generate_video`, `make_long_video` and `check_job`.

## Setup

1. Install the plugin: from the Claude directory once it is listed, or in Claude Code with

   ```
   /plugin marketplace add opentech-dev/tesseract-claude-plugin
   /plugin install tesseract@tesseract
   ```
2. The first time Claude uses Tesseract, a Tesseract page opens. Sign in with your Tesseract account (or create one
   at [app.tesseract.dev](https://app.tesseract.dev)) and press **Approve** on the page that names Claude.
3. Ask, for example:
   - "Make a 15-second 9:16 ad for our bakery from this photo: a slow push-in, steam rising, our name at the end."
   - "Show me Tesseract's portrait effects, then apply one to this selfie."
   - "Make four shots of this mug on marble in morning light."

The full guide, with the same steps for other apps, is at [tesseract.dev/mcp](https://tesseract.dev/mcp/).

## Other apps

The same repository installs in other agents:

| App | Install |
|---|---|
| Gemini CLI | `gemini extensions install https://github.com/opentech-dev/tesseract-claude-plugin` |
| Cursor | Add it from the Cursor Marketplace once listed, or point Cursor at this repository (`.cursor-plugin/plugin.json`, `mcp.json`) |
| Any agent that reads skills | `npx skills add opentech-dev/tesseract-claude-plugin` |
| Any MCP app | Add the remote server `https://app.tesseract.dev/api/core/tesseract/mcp` (Streamable HTTP, OAuth); guide at [tesseract.dev/mcp](https://tesseract.dev/mcp/) |

## Cost

Each picture, effect or video is charged to your Tesseract plan: its free media first, then its allowance or balance.
The skills tell Claude to state the price and agree a ceiling with you before starting a job, and to pass that ceiling
as `max_usd`, so a job that would cost more is never started. Each app you connect also has its own monthly spending
limit, which you set in Tesseract under Settings → Account → Connected apps.

## Privacy

This plugin contains no code that runs on your computer: no hooks, no scripts, no local server. It only points Claude
at Tesseract's hosted connector and gives Claude written instructions (the two skills).

**What is sent, and where:**

- **To Tesseract** (`app.tesseract.dev`, operated by Eightcell Labs, Inc.): what Claude puts into a tool call. That is
  your instructions for the job, the pictures or video you give it (as public links or as image data), and the
  settings (shape, length, model, effect, cost ceiling). Signing in sends your Tesseract sign-in to Tesseract's own
  page, never to Claude.
- **To media model providers, through Tesseract:** to make the result, Tesseract sends the job's instructions and
  pictures to the model provider that runs the chosen model: fal.ai (which runs picture, effect and video models from
  several model makers) or Google (Gemini video).
- **Fetched by Tesseract:** a picture or video you give as a public `https://` link is downloaded by Tesseract's
  server (public addresses only, up to 10 MB for a picture) so the model can use it.
- **Back to Claude:** the job's status, its price, and download links to the results, valid for one hour.

**What Tesseract never receives:** your Claude conversation beyond what Claude puts into a tool call, Claude's memory,
or your files. The connector cannot read your Tesseract conversations, files or settings either.

**What is kept:** Tesseract keeps a record of each job and its billing record in your account, and a record of the
connection (the app's name, when it was connected and last used, its monthly limit and what it spent this month).

**Your controls:** disconnect Claude at any time in Tesseract under Settings → Account → Connected apps. Changing your
password or deleting your account disconnects every app.

Full policy: [tesseract.dev/privacy](https://tesseract.dev/privacy/). Terms: [tesseract.dev/terms](https://tesseract.dev/terms/).

## Support

Write to [ops@tesseract.dev](mailto:ops@tesseract.dev) or use [tesseract.dev/contact](https://tesseract.dev/contact/).

## License

MIT. See [LICENSE](LICENSE).
