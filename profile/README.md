<p align="center">
  <img src="banner-3.svg" alt="ScriptHaul: YouTube transcripts, in bulk." width="100%">
</p>

<p align="center">
  <a href="https://scripthaul.com"><img src="https://img.shields.io/badge/Free%20site-scripthaul.com-2d5c47?style=for-the-badge" alt="Free site"></a>
  <a href="https://api.scripthaul.com/docs"><img src="https://img.shields.io/badge/API%20docs-quickstart-1e3a2d?style=for-the-badge" alt="API docs"></a>
  <a href="https://api.scripthaul.com/#get-key"><img src="https://img.shields.io/badge/API%20key-100%20free%20credits%20a%20month-8ebba1?style=for-the-badge&labelColor=1e3a2d" alt="Get an API key"></a>
  <a href="https://api.scripthaul.com/docs/mcp"><img src="https://img.shields.io/badge/MCP-connect%20your%20assistant-2d5c47?style=for-the-badge" alt="MCP setup"></a>
  <a href="https://github.com/scripthaul/scripthaul-js/blob/main/LICENSE"><img src="https://img.shields.io/badge/clients%20%26%20tools-MIT-f2c53d?style=for-the-badge&labelColor=1e3a2d" alt="MIT license"></a>
</p>

## What ScriptHaul is

ScriptHaul turns public YouTube videos into clean transcript files, one video or a whole channel at a time.

- **[scripthaul.com](https://scripthaul.com)** is free and needs no account. Paste a video, playlist, or channel; every available caption comes back as TXT, SRT, VTT, Markdown, or timed JSON, with a manifest that says exactly what happened to each video.
- **[The ScriptHaul API](https://api.scripthaul.com)** is the same engine for developers and AI agents: whole-channel bulk jobs, search inside what was said, channel libraries you can query, monitors for new uploads, and an MCP server. Pay as you go, credits never expire, cache hits and failures cost nothing, 100 free credits a month.
- **Honest by design.** Every transcript is labelled: manual or auto-generated captions, the language you asked for versus the language you got, and why a video produced nothing. Nothing is silently skipped, and no video or audio is ever downloaded.

## Open source here

Everything a developer touches is MIT-licensed in this organization. The service itself is not open source.

| Repository | What it is | Install |
| --- | --- | --- |
| [scripthaul-js](https://github.com/scripthaul/scripthaul-js) | Dependency-free JavaScript client for the API | `npm install github:scripthaul/scripthaul-js` |
| [scripthaul-python](https://github.com/scripthaul/scripthaul-python) | Standard-library-only Python client | `pip install git+https://github.com/scripthaul/scripthaul-python` |
| [agent-skills](https://github.com/scripthaul/agent-skills) | The skill that teaches Claude, Cursor, and other agents to use ScriptHaul | `npx skills add scripthaul/agent-skills --skill scripthaul-transcripts` |
| [youtube-caption-formats](https://github.com/scripthaul/youtube-caption-formats) | The caption converters behind every download: json3, WebVTT, and TTML to text, SRT, VTT, Markdown, and timed JSON | `npm install github:scripthaul/youtube-caption-formats` |
| [scripthaul-extension](https://github.com/scripthaul/scripthaul-extension) | The Chrome and Edge extension, one click from any YouTube page | [Chrome Web Store](https://chromewebstore.google.com/detail/pcimcldhfdhjbgjbihmccbbehbpbinhf), or load unpacked |
| [openapi](https://github.com/scripthaul/openapi) | The API's OpenAPI 3.1 description, generated from the router | Generate a client in any language |

## Thirty seconds

```sh
curl --get https://api.scripthaul.com/v1/transcript \
  -H "Authorization: Bearer $SCRIPTHAUL_API_KEY" \
  --data-urlencode "video_id=jNQXAC9IVRw" \
  --data-urlencode "format=srt"
```

```js
import ScriptHaul from 'scripthaul';

const client = new ScriptHaul({ apiKey: process.env.SCRIPTHAUL_API_KEY });
const job = await client.jobs.create({ input: 'https://www.youtube.com/@example' });
await job.wait(); // every transcript of the channel, one job
```

Or connect an assistant instead of writing code: [MCP setup for Claude, Cursor, ChatGPT, VS Code, and others](https://api.scripthaul.com/docs/mcp).

## Support

- Docs: [api.scripthaul.com/docs](https://api.scripthaul.com/docs)
- Status: [scripthaul.com/status](https://scripthaul.com/status)
- Email: support@scripthaul.com
- Bugs in a client or tool: open an issue in that repository.
