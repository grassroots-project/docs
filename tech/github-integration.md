# GitHub 集成

Grassroots Project 使用 GitHub Issues 作为核心数据源。

## 为什么用 GitHub Issues？

- 免费、可靠
- 天然的版本控制
- 开放 API
- 支持 Markdown
- 有成熟的协作功能（评论、标签、Assignee）

## 数据结构

### 任务池

每个任务是一个 Issue，使用标签分类：

| 标签 | 说明 |
|------|------|
| P0, P1, P2 | 优先级 |
| 待领, 进行中, 已完成 | 状态 |
| 文案, 设计, 技术, 运营... | 技能标签 |

### 人才库

Issue #1 存放成员列表，使用 Markdown 格式：

```markdown
### 成员名

- **加入时间**：YYYY-MM-DD
- **技能标签**：...
- **时间承诺**：每周 Xh
- **当前任务**：#编号
- **历史贡献**：...
```

### 资源池

Issue #2 存放资源列表：

```markdown
### 资源名

- **资源类型**：比特币/知识/工具/人力
- **描述**：...
- **当前状态**：可用/已占用/待规划
- **负责人**：...
- **使用说明**：...
- **链接**：...
```

## API 使用

### 获取 Issues

```javascript
const response = await fetch(
  'https://api.github.com/repos/grassroots-project/tasks/issues?state=open',
  { headers: { 'Accept': 'application/vnd.github.v3+json' } }
);
const issues = await response.json();
```

### 认证请求

需要修改 Issue 时，使用 Personal Access Token：

```javascript
const response = await fetch(url, {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${token}`,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(data)
});
```

### 常用操作

| 操作 | API |
|------|-----|
| 获取 Issues | GET /repos/{owner}/{repo}/issues |
| 获取单个 Issue | GET /repos/{owner}/{repo}/issues/{number} |
| 添加评论 | POST /repos/{owner}/{repo}/issues/{number}/comments |
| 更新标签 | PUT /repos/{owner}/{repo}/issues/{number}/labels |
| 添加 Assignee | POST /repos/{owner}/{repo}/issues/{number}/assignees |

## 权限

用户登录需要 GitHub PAT，需要 `public_repo` 权限。

Token 仅存储在用户浏览器本地，不上传服务器。

## 仓库列表

| 仓库 | 用途 |
|------|------|
| grassroots-project/website | 项目网站 |
| grassroots-project/tasks | 任务池、人才库、资源池 |
| grassroots-project/docs | 文档 |
