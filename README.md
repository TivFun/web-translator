## Minimalist AI Translator (Tampermonkey)

A small, fast userscript that translates selected text on any webpage using your preferred AI provider. Designed for minimal friction: select text, hover the blue icon, get a translation popup, copy if needed, click outside to dismiss.

- **Sub‑readme ([中文](README.zh-CN.md))**: See `README.zh-CN.md`

### Features
- **One‑gesture translate**: select → hover icon → translation box appears near the cursor
- **macOS‑style popup** with copy button and typography‑friendly rendering
- **British English translation mode** with British spelling and expressions
- **Format‑aware prompting** to preserve headings and paragraphs where possible
- **Multiple providers**: OpenAI, Gemini, Anthropic, Grok, DeepSeek, Qwen, Doubao
- **Local settings** using Tampermonkey storage; no third‑party servers
- **Fine control**: icon delay and popup width

### Quick start
1. **Install Tampermonkey**
   - Chrome/Edge/Firefox/Safari: install the Tampermonkey extension from each browser’s store.
2. **Create the userscript**
   - Tampermonkey Dashboard → Create a new script → replace the template with `translator.js` content → Save.
3. **Grant permissions if prompted**
4. **Open settings**
   - Tampermonkey menu → “Open Translator Settings”.
5. **Configure**
   - Choose provider, paste your API key, pick a model (or keep the default), set target language and UI language.

### How to use
- Select any text on a webpage.
- After a short delay, a blue circular icon appears by the cursor.
- Hover the icon to trigger translation.
- A popup appears near the cursor with the translation.
- Click the button to copy; click outside the popup to close.

### Settings explained
- **文/A (Interface Language)**: UI language of the settings (English or 中文).
- **AI**: Provider (ChatGPT, Gemini, Claude, Grok, DeepSeek, Qwen, Doubao).
- **Model**: Model name as the provider expects (e.g. `gpt-4o-mini`, `gemini-2.0-flash`).
- **API Key**: Your provider API key (stored locally by Tampermonkey).
- **Target Language**: `Chinese`, `Japanese`, or `English (British)` style.
- **Icon Display Delay**: Delay before showing the blue icon after selection.
- **Translation Box Max Width**: Max width of the popup in pixels.

### Supported providers and default models
If you leave the model empty, the script uses a sensible default:
- **OpenAI**: `gpt-3.5-turbo`
- **Gemini**: `gemini-2.0-flash`
- **Anthropic**: `claude-3-haiku-20240307`
- **Grok (xAI)**: `grok-2-latest`
- **DeepSeek**: `deepseek-chat`
- **Qwen**: `qwen-plus`
- **Doubao**: `doubao-lite`

### Permissions
This userscript runs on all sites and requests only what it needs. Key metadata includes:

```1:23:translator.js
// ==UserScript==
// @name         Minimalist AI Translator (Tampermonkey Version)
// @match        *://*/*
// @exclude      https://chrome.google.com/webstore/*
// @exclude      https://addons.mozilla.org/*
// @grant        GM_getValue
// @grant        GM_setValue
// @grant        GM_xmlhttpRequest
// @grant        GM_registerMenuCommand
// @grant        GM_addStyle
// @run-at       document-end
// @connect      api.openai.com
// @connect      generativelanguage.googleapis.com
// @connect      api.anthropic.com
// @connect      api.x.ai
// @connect      api.deepseek.com
// @connect      dashscope.aliyuncs.com
// @connect      ark.cn-beijing.volces.com
// ==/UserScript==
```

If you use a different API endpoint (e.g. Azure OpenAI), add its domain to `@connect`.

### Privacy & security
- Your **API key is stored locally** via Tampermonkey storage (`GM_getValue/GM_setValue`).
- Requests are sent directly to your chosen **AI API** via `GM_xmlhttpRequest`.
- The script does not send data to any third‑party servers beyond your chosen provider.

