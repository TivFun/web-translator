# Web-Translator

[English](README.md) | [中文](README_zh.md)

A tiny userscript that translates any text you select on a web page using an AI model of your choice. Select some text, hover over the little icon that pops up, and the translation appears right there.

No accounts, no servers — it talks to the AI provider's API directly from your browser, using **your own API key**.

## Preview

![Screenshot](https://github.com/user-attachments/assets/eabc3813-27cf-4643-9563-915d5095abc2)
![Screenshot](https://github.com/user-attachments/assets/a53295df-60be-4bb1-a40c-fcb41eaa0bdc)
![Screenshot](https://github.com/user-attachments/assets/034907bb-bbff-4e9c-99c2-f9be52a4f7d2)

## Features

- Translate selected text into **Chinese, Japanese, or English**.
- Works with many AI providers out of the box: **ChatGPT, Gemini, Claude, Grok, DeepSeek, Qwen, Doubao**.
- **Add any other provider yourself, from the settings panel** — no code editing. If it speaks the OpenAI API format (most do), just paste its endpoint URL.
- Each provider remembers its **own API key**, so you can switch between them freely.
- English / Chinese interface.

## Installation (2 steps)

You need the [Tampermonkey](https://www.tampermonkey.net/) browser extension. It runs userscripts like this one. It's free and works on Chrome, Edge, Firefox, Safari, and others.

1. **Install Tampermonkey** from your browser's extension store (or [tampermonkey.net](https://www.tampermonkey.net/)).
2. **Install this script:** open [`web-translator-script.js`](web-translator-script.js), copy everything, then in the Tampermonkey dashboard go to **+ (Create a new script)**, paste it in, and press **Ctrl/Cmd + S** to save.

That's it — the script is now active on every page.

## Setup (2 steps)

1. Click the **Tampermonkey icon** in your toolbar → **Open Translator Settings**.
2. Under **Select AI**, pick a provider, paste its **API Key**, and click **Save Settings**.

That's all you need for the built-in providers. (The **Model** field is filled with a sensible default — you only change it if you want a specific model.)

### Where do I get an API key?

You get a key from the provider's own website. A few common ones:

| Provider | Get your key at |
| --- | --- |
| ChatGPT (OpenAI) | platform.openai.com |
| Gemini (Google) | aistudio.google.com |
| Claude (Anthropic) | console.anthropic.com |
| DeepSeek | platform.deepseek.com |
| Grok (xAI) | console.x.ai |

Most providers charge per use, but it's usually very cheap for short translations.

## Adding your own provider

Want to use a provider that isn't in the list (e.g. Moonshot/Kimi, Together, a local Ollama server)? You don't need to touch the code:

1. In settings, open the **Select AI** dropdown and choose **➕ Add custom provider…**.
2. Fill in:
   - **Name** — anything you like (e.g. `Moonshot`).
   - **Type** — almost always `OpenAI-compatible`. Use `Gemini` or `Anthropic` only for those specific APIs.
   - **API endpoint URL** — from the provider's docs, e.g. `https://api.moonshot.cn/v1/chat/completions`.
   - **Default model** (optional) — e.g. `moonshot-v1-8k`.
3. Click **Add Provider**. It's now selected automatically — just paste its API key and save.

You can **edit** or **delete** custom providers anytime from that same panel.

> The first time the script contacts a new domain, Tampermonkey asks you to confirm the connection. This is normal — it's letting you see exactly where the script is sending data.

## Usage

1. **Select** some text on any page.
2. A small translation icon appears next to it — **hover** over it.
3. The translation pops up. Click **Copy** to copy it, or click anywhere else to dismiss.

## Privacy

The text you select is sent directly to the AI provider you chose, using your API key. Nothing passes through any third-party server. Your API keys are stored locally by Tampermonkey on your own machine.
