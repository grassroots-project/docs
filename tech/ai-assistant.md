# AI 助手

Grassroots Project 的 AI 助手技术文档。

## 概述

AI 助手提供对话式交互，帮助用户：
- 了解项目
- 推荐任务
- 引导加入流程

## 技术架构

```
用户 → 网页前端 → OpenAI 兼容 API → LLM
```

## 支持的 API

任何 OpenAI 兼容的 API 都可以使用：

| 服务商 | Endpoint | 模型示例 |
|--------|----------|----------|
| Moonshot | https://api.moonshot.cn/v1 | moonshot-v1-8k |
| DeepSeek | https://api.deepseek.com/v1 | deepseek-chat |
| 智谱 GLM | https://open.bigmodel.cn/api/paas/v4 | glm-4-flash |
| OpenAI | https://api.openai.com/v1 | gpt-4o-mini |

## 配置

用户需要配置：
- **Endpoint**：API 地址
- **Model**：模型名称
- **API Key**：密钥

配置存储在浏览器 localStorage：
- `grassroots_api_endpoint`
- `grassroots_api_model`
- `grassroots_api_key`

## 系统 Prompt

AI 助手使用预设的系统 Prompt，包含：

1. **角色定义**：Grassroots Project 的 AI 助手
2. **项目知识库**：愿景、三条腿、池塘模式等
3. **任务列表**：动态从 GitHub API 加载
4. **回答风格**：简洁、友好、使用 emoji

## 任务推荐

AI 助手可以根据用户描述推荐任务：

```
用户：我会写代码，有什么任务适合我？

AI：根据你的技能，推荐以下任务：
- #X [TASK] ... | P1 | 技术
- #Y [TASK] ... | P2 | 技术
```

## 安全考虑

- API Key 仅存储在用户浏览器
- 不经过任何中间服务器
- 用户完全控制自己的 API 使用

## 开发

AI 助手代码在 `pages/assistant.html`。

关键函数：
- `getApiConfig()` - 获取 API 配置
- `sendMessage()` - 发送消息
- `loadTasks()` - 加载任务列表
- `formatTasksForPrompt()` - 格式化任务用于 Prompt
