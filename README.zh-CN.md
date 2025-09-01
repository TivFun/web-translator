## 极简 AI 划词翻译（Tampermonkey 版）

一款小而快的划词翻译用户脚本。选中文本，稍等片刻光标旁会出现蓝色圆形图标，鼠标悬停即可弹出翻译气泡框，支持复制后关闭。

### 功能特点

- **极简手势**：选中文本 → 悬停蓝色图标 → 显示翻译
- **macOS 风格弹窗**，排版友好，带复制按钮
- **英式英文模式**（英式拼写与表达）
- **尽量保持原始格式**（标题、段落提示）
- **多家模型提供商**：OpenAI、Gemini、Anthropic、Grok、DeepSeek、Qwen、豆包
- **本地设置存储**，不经第三方服务器
- **可调节**：图标延迟与弹窗最大宽度

### 快速开始

1. **安装 Tampermonkey**（各浏览器扩展商店）
2. **创建用户脚本**
   - 打开 Tampermonkey 控制台 → 新建脚本 → 用 `translator.js` 全部内容替换 → 保存
3. **如有提示请授予权限**
4. **打开设置**
   - Tampermonkey 菜单 → “打开翻译器设置”
5. **完成配置**
   - 选择提供商、填入 API Key、填写或保留默认模型、选择目标语言与界面语言

### 使用方法

- 在任意网页选中文本；
- 稍候光标旁出现蓝色圆形图标；
- 鼠标悬停在图标上触发翻译；
- 翻译结果以气泡形式显示在光标附近；
- 可点击按钮复制；点击气泡外任意处关闭。

### 设置项说明

- **文/A（界面语言）**：设置界面使用中文或 English
- **AI（提供商）**：ChatGPT、Gemini、Claude、Grok、DeepSeek、Qwen、豆包
- **模型**：提供商要求的模型名（如 `gpt-4o-mini`、`gemini-2.0-flash`）
- **API 密钥**：你的提供商 API Key（Tampermonkey 本地存储）
- **翻译目标语言**：中文、日语、英式英文
- **图标显示延迟**：选中文本后，图标出现的延迟
- **翻译框最大宽度**：气泡最大宽度（像素）

### 支持的提供商与默认模型

若留空“模型”，脚本会使用默认值：

- **OpenAI**：`gpt-3.5-turbo`
- **Gemini**：`gemini-2.0-flash`
- **Anthropic**：`claude-3-haiku-20240307`
- **Grok (xAI)**：`grok-2-latest`
- **DeepSeek**：`deepseek-chat`
- **Qwen**：`qwen-plus`
- **豆包（Doubao）**：`doubao-lite`

### 权限

脚本在所有站点运行，仅请求必要权限。核心元数据如下：

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

如使用其他域名（如 Azure OpenAI），请将其加入 `@connect`。

### 隐私与安全

- **API Key 仅存储在本地**（Tampermonkey 的 `GM_getValue/GM_setValue`）
- 通过 `GM_xmlhttpRequest` 直接向你选择的 **AI API** 发起请求
- 除你的 AI 提供商外，脚本不会向第三方服务器上报数据
