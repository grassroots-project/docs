# 网站架构

Grassroots Project 网站的技术架构。

## 技术栈

| 层面 | 技术 |
|------|------|
| 前端 | 纯静态 HTML/CSS/JS |
| 部署 | GitHub Pages |
| 数据 | GitHub Issues API |
| AI | OpenAI 兼容 API（Kimi/DeepSeek/GLM 等） |
| Markdown 渲染 | marked.js |

## 项目结构

```
website/
├── index.html              # 首页
├── README.md               # 项目说明
├── assets/
│   ├── css/
│   │   └── styles.css      # 公共样式
│   └── js/
│       ├── auth.js         # GitHub PAT 认证
│       ├── task-actions.js # 任务操作
│       └── gh-api.js       # GitHub API 封装
└── pages/
    ├── about.html          # 关于
    ├── tasks.html          # 任务池
    ├── kanban.html         # 看板
    ├── people.html         # 人才库
    ├── resources.html      # 资源池
    ├── assistant.html      # AI 助手
    └── join.html           # 加入我们
```

## 关键功能

### 任务池 (tasks.html)

- 从 GitHub Issues API 获取任务列表
- 支持按优先级/状态筛选
- GitHub PAT 登录
- 一键领取/放弃/完成任务

### 看板 (kanban.html)

- 三列视图：待领/进行中/已完成
- 实时同步 Issues 状态
- 每 30 秒自动刷新

### 人才库 (people.html)

- 从 Issues 自动提取成员信息
- 显示每人的任务参与情况
- 活动流展示最近动态

### 资源池 (resources.html)

- 解析 Issue #2 中的资源列表
- 资源卡片展示
- 按类型筛选

### AI 助手 (assistant.html)

- 支持任意 OpenAI 兼容 API
- 用户自己配置 Endpoint/Model/Key
- 内置项目知识库
- 动态加载任务列表用于推荐

## 本地开发

```bash
# 克隆仓库
git clone https://github.com/grassroots-project/website.git
cd website

# 启动本地服务器
python -m http.server 8000

# 访问 http://localhost:8000
```

## 部署

推送到 `main` 分支后自动部署到 GitHub Pages。

```bash
git add .
git commit -m "update"
git push origin main
```

部署 URL: https://grassroots-project.github.io/website/
