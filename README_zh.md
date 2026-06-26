# Web-Translator 网页翻译器

[English](README.md) | [中文](README_zh.md)

一个超轻量的油猴脚本（userscript），用你选定的 AI 模型翻译网页上的任意文字。选中文字，把鼠标移到弹出的小图标上，译文就出现在原地。

无需注册、无需服务器——它用**你自己的 API 密钥**，直接从浏览器调用 AI 服务商的接口。

## 预览

![截图](https://github.com/user-attachments/assets/eabc3813-27cf-4643-9563-915d5095abc2)
![截图](https://github.com/user-attachments/assets/a53295df-60be-4bb1-a40c-fcb41eaa0bdc)
![截图](https://github.com/user-attachments/assets/034907bb-bbff-4e9c-99c2-f9be52a4f7d2)

## 功能特点

- 将选中的文字翻译成**中文、日语或英语**。
- 内置支持多家 AI 服务商：**ChatGPT、Gemini、Claude、Grok、DeepSeek、Qwen（通义千问）、Doubao（豆包）**。
- **可在设置面板里自行添加任意其他服务商**，无需改代码。只要它兼容 OpenAI 接口格式（大多数都兼容），把接口地址粘进去就行。
- 每个服务商各自记住**自己的 API 密钥**，可以随意切换。
- 中 / 英界面切换。

## 安装（两步）

你需要先装 [Tampermonkey（油猴）](https://www.tampermonkey.net/) 浏览器扩展，它负责运行这类用户脚本。免费，支持 Chrome、Edge、Firefox、Safari 等。

1. **安装 Tampermonkey**：从浏览器的扩展商店安装，或访问 [tampermonkey.net](https://www.tampermonkey.net/)。
2. **安装本脚本**：打开 [`web-translator-script.js`](web-translator-script.js)，全选复制；在 Tampermonkey 管理面板点 **「+」（新建脚本）**，粘贴进去，按 **Ctrl/Cmd + S** 保存。

完成——脚本现在已在所有网页上生效。

## 配置（两步）

1. 点击工具栏上的 **Tampermonkey 图标** → **打开翻译器设置**。
2. 在**「选择 AI」**里选一个服务商，粘贴它的 **API 密钥**，点**「保存设置」**。

内置服务商到这一步就能用了。（**「模型」**字段已自动填好默认模型，除非你想指定某个特定模型，否则不用改。）

### API 密钥去哪里拿？

密钥要去各服务商自己的网站申请。几个常见的：

| 服务商 | 申请地址 |
| --- | --- |
| ChatGPT（OpenAI） | platform.openai.com |
| Gemini（Google） | aistudio.google.com |
| Claude（Anthropic） | console.anthropic.com |
| DeepSeek（深度求索） | platform.deepseek.com |
| Qwen（通义千问） | dashscope.console.aliyun.com |
| Doubao（豆包） | console.volcengine.com |

大多数服务商按用量计费，但翻译这种短文本通常很便宜。

## 添加自己的服务商

想用列表里没有的服务商（比如 Moonshot/Kimi、Together、本地的 Ollama）？不用碰代码：

1. 在设置里展开**「选择 AI」**下拉框，选 **「➕ 添加自定义服务商…」**。
2. 填写：
   - **名称** —— 随便起（如 `Moonshot`）。
   - **类型** —— 绝大多数选 `OpenAI-compatible`；只有对应的那两种 API 才选 `Gemini` 或 `Anthropic`。
   - **API 接口地址** —— 来自服务商文档，如 `https://api.moonshot.cn/v1/chat/completions`。
   - **默认模型**（可选）—— 如 `moonshot-v1-8k`。
3. 点**「添加服务商」**，它会被自动选中——接着粘贴 API 密钥并保存即可。

之后随时能在同一面板里**编辑**或**删除**自定义服务商。

> 脚本首次连接一个新域名时，Tampermonkey 会弹窗让你确认。这是正常的——它在让你清楚看到数据被发往哪里。

## 使用方法

1. 在任意网页上**选中**一段文字。
2. 旁边会出现一个小翻译图标——把鼠标**悬停**上去。
3. 译文弹出。点**「复制」**可复制，点其他地方即可关闭。

## 隐私说明

你选中的文字会用你的密钥直接发给你所选的 AI 服务商，不经过任何第三方服务器。API 密钥由 Tampermonkey 保存在你自己的电脑本地。
